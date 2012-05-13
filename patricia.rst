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

.. c:function:: mowgli_patricia_t (mowgli_patricia_create_named(const char *name, void (*canonize_cb)(char *key))

This function generates a new patricia with the specified name.
