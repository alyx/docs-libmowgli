mowgli.list
===========

.. c:function:: void mowgli_node_bootstrap(void)

This function initialises the node and list heaps. If either heap cannot be
allocated, the program will abort.

.. c:function:: mowgli_node_t *mowgli_node_create(void)

This function allocates a new empty node from the node heap
and returns a pointer to it.

.. c:function:: void mowgli_node_free(mowgli_node_t *n)

This function accepts one parameter, a mowgli_node_t object, and
deallocates it, returning the allocated memory to the node heap.

.. c:function:: void mowgli_node_add(void *data, mowgli_node_t *n, mowgli_list_t *l)

This function accepts three parameters, a pointer to the data to store in
a node, an allocated mowgli_node_t object, and the list to add this node to.

.. c:function:: void mowgli_node_add_head(void *data, mowgli_node_t *n, mowgli_list_t *l)

This function is the same as :c:func:`mowgli_node_add`, differing
only in that this function prepends the node to the head of the list.

.. c:function:: void mowgli_node_add_before(void *data, mowgli_node_t *n, mowgli_list_t *l, mowgli_node_t *before)

This function works like :c:func:`mowgli_node_add`, however this function
inserts the new node directly before the node pointed to by "before"
in the list.

.. c:function:: void mowgli_node_add_after(void *data, mowgli_node_t *n, mowgli_list_t *l, mowgli_node_t *before)

This function is identical to :c:func:`mowgli_node_add_before`, differing in
that this function adds the new node directly after the node pointed to by
the "before" parameter.

.. c:function:: mowgli_node_t *mowgli_node_nth(mowgli_list_t *l, size_t pos)

This function returns a pointer to the mowgli_node_t object at "pos" position
in the specified list.

.. c:function:: void *mowgli_node_nth_data(mowgli_list_t *l, size_t pos)

This function returns a pointer to the data contained in the node at "pos"
position in the specified list.

.. c:function:: void mowgli_node_insert(void *data, mowgli_node_t *n, mowgli_list_t *l, size_t pos)

This function inserts a node containing the specified data into
the list "l" at "pos" position.

.. c:function:: ssize_t mowgli_node_index(mowgli_node_t *n, mowgli_list_t *l)

This function returns the position of the specified node in list "l."

.. c:function:: void mowgli_node_delete(mowgli_node_t *n, mowgli_list_t *l)

This function removes node "n" from the specified list. It does not delete the
node itself, however.

.. c:function:: mowgli_node_t *mowgli_node_find(void *data, mowgli_list_t *l)

This function searches through list "l" until it locates a node containing
the specified data. If this node is found, it returns a pointer to said node.
If unfound, this function returns NULL.

.. c:function:: void mowgli_node_move(mowgli_node_t *m, mowgli_list_t *oldlist, mowgli_list_t *newlist)

This function moves node "m" from the list pointed to by "oldlist" to the
list pointed to by "newlist."

.. c:function:: mowgli_list_t *mowgli_list_create(void)

This function creates a new list, returning a pointer to the allocated list.

.. c:function:: void mowgli_list_free(mowgli_list_t *l)

This function deallocates the list itself, returning the used memory
to the list heap.

.. c:function:: void mowgli_list_concat(mowgli_list_t *l, mowgli_list_t *l2)

This function concatenates two lists together, merging the content of list "l2"
into list "l."

.. c:function:: void mowgli_list_reverse(mowgli_list_t *l)

This function reverses the order of the nodes in the specified list.

.. c:function:: void mowgli_list_sort(mowgli_list_t *l, mowgli_list_comparator_t comp, void *opaque)

This function sorts through list "l" using the function pointed to by "comp."

.. c:type:: mowgli_node_t

This type is a typedef of a structure containing two pointers, one to the next
mowgli_node_t object in the list and one to the previous mowgli_node_t object,
as well as a pointer to the data stored in this node.

.. c:type:: mowgli_list_t

This type is a typedef of a structure containing two pointers, one to the head,
or first node, of the list and one to the tail, or last node, of the list. This
type also contains a size_t object specifying the amount of nodes in the list.

.. c:type:: mowgli_list_comparator_t

This type is a typedef of a function pointer. This function type accepts three
parameters. The first two parameters are the nodes to compare, the third is a
pointer to an opaque variable. This type will return an integer.

.. c:macro:: MOWGLI_LIST_FOREACH(n, head)

This macro, going through the node n, iterates through the list in a for loop.

.. c:macro:: MOWGLI_LIST_FOREACH_NEXT(n, head)

This macro does the same as :c:macro:`MOWGLI_LIST_FOREACH`, ending when
the next node would be NULL, instead of when the current node becomes NULL.

.. c:macro:: MOWGLI_LIST_FOREACH_PREV(n, tail)

This macro functions the same as :c:macro:`MOWGLI_LIST_FOREACH_NEXT`, however
this macro iterates up the list from the tail to the head, ending when the
previous node (The node before the current) is NULL.

.. c:macro:: MOWGLI_LIST_LENGTH(list)

This macro returns the size of the list, contained in the count variable
of :c:type:`mowgli_list_t`.

