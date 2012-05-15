mowgli.patricia
===============

A radix trie that avoids one-way branching and redundant nodes.

To find a node, the tree is traversed starting from the root. The
nibnum in each node indicates which nibble of the key needs to be
tested, and the appropriate branch is taken.

The nibnum values are strictly increasing while going down the tree.

.. c:function:: mowgli_patricia_t *mowgli_patricia_create(void (*canonize_cb)(char *key))

This function generates a new patricia object. It accepts one parameter,
a function to use for canonising keys (E.g., use a function that makes
the string upper case to create a patricia with case-insensitive matching).
This function will return a pointer to a patricia object.

If there is not available memory to allocate the object,
the program will abort.

.. c:function:: mowgli_patricia_t mowgli_patricia_create_named(const char *name, void (*canonize_cb)(char *key))

This function generates a new patricia with the specified name. It accepts
two parameters, the name of the trie and a function to use for canonising keys.

If there is not available memory to allocate the object,
the program will abort.

.. c:function:: void mowgli_patricia_shutdown(void)

This function is used to clean up post-patricia usage, ensuring all used
memory is released as soon as possible by deallocating the allocated
patricia storage heaps.

.. c:function:: void mowgli_patricia_destroy(mowgli_patricia_t *dtree, void (*destroy_cb)(const char *key, void *data, void *privdata), void *privdata)

This function recursively destroys all nodes in the patricia tree, "dtree."
It accepts three parameters: the patricia tree to destroy, an iteration
callback (These are sent the data contained within the nodes of the patricia
tree, where they can be dealt with accordingly) and variable to contain additional
private data to be passed to the callback.

If this function is called without a callback, the objects bound to the tree
will not be destroyed.

.. c:function:: void mowgli_patricia_foreach(mowgli_patricia_t *dtree, int(*foreach_cb)(const char *key, void *data, void *privdata), void *privdata)

This function iterates over all entries in the specified patricia tree,
passing the key and value of each node to the specified callback function, 
along with the private variable passed in privdata.

.. c:function:: void *mowgli_patricia_search(mowgli_patricia_t *dtree, void *(*foreach_cb)(const char *key, void *data, void *privdata), void *privdata)

This function searches through all entries in the specified patricia tree,
using a custom callback. This will iterate through the tree until the
conditions are met. This function takes three parameters, the tree to search
through, a function pointer to the callback each entry will be sent to and
a variable which may hold whatever private data needs to be continually sent
to the callback function.

.. c:function:: mowgli_boolean_t mowgli_patricia_add(mowgli_patricia_t *dict, const char *key, void *data)

This function creates a new node of name "key" within the specified patricia
tree, filling the node with the specified data. 

This function will return :c:type:`TRUE` on success and :c:type:`FALSE` on failure.

.. c:function:: void *mowgli_patricia_delete(mowgli_patricia_t *dict, const char *key)

This function will delete the node of name "key" from the specified tree.
On success, this function will return a pointer to the data stored within the
node, which must then be deallocated manually. On failure, this function will
return NULL.

.. c:function:: void *mowgli_patricia_retrieve(mowgli_patricia_t *dtree, const char *key)

This function retrieves the data stored in the node "key" from the patricia
tree "dtree" and returns a pointer to it on success. On failure, this function
returns NULL.

.. c:function:: unsigned int mowgli_patricia_size(mowgli_patricia_t *dict)

This function returns an unsigned integer containing the size of the specified
patricia tree.

.. c:macro:: MOWGLI_PATRICIA_FOREACH(element, state, dict)

This is a convenience macro for inlining iteration of dictionaries.
This macro will iterate through a patricia tree as a for() loop.

.. c:type:: mowgli_patricia_t

This is a typedef of the mowgli_patricia_ structure. This type contains
a pointer to the function used for canonizing keys, a pointer to the
root element of the tree, an integer containing the size of the tree and
a string containing the name of the tree.

