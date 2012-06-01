mowgli.dictionary
=================

.. c:function:: mowgli_dictionary_t *mowgli_dictionary_create(mowgli_dictionary_comparator_func_t compare_cb)

This function creates and allocates a new dictionary object. 
If it cannot allocate the required memory,it will cause 
the program to abort. This function accepts one parameter, 
a :c:type:`mowgli_dictionary_comparator_func_t`
callback to the function used for comparing entries within the 
dictionary. On success, this function returns a new dictionary object.

.. c:function:: mowgli_dictionary_t *mowgli_dictionary_create_named(const char *name, mowgli_dictionary_comparator_func_t compare_cb)

This function creates an allocates a named dictionary object.
It accepts two parameters, the name of the dictionary and an
entry comparing callback. It returns a pointer to the dictionary
on success.

.. c:function:: void mowgli_dictionary_set_comparator_func(mowgli_dictionary_t *dict, mowgli_dictionary_comparator_func_t compare_cb)

This function changes the comparator function used by the
specified dictionary to the newly passed function.

.. c:function:: mowgli_dictionary_comparator_func_t mowgli_dictionary_get_comparator_func(mowgli_dictionary_t *dict)

This function accepts a pointer the a :c:type:`mowgli_dictionary_t`
object and returns the comparator callback for that object.

.. c:function:: int mowgli_dictionary_get_linear_index(mowgli_dictionary_t *dict, const void *key)

This function accepts two parameters. The first is a dictionary object,
the second is a pointer to a key to search for in the dictionary.
This function attempts to locate the position of the key in the dictionary.
If the key is is not found in the dictionary, this function returns -1.
If either the dictionary or key are NULL, this function returns 0.
The function will otherwise return an integer specifying the position
of the given key within the dictionary.

.. c:function:: void mowgli_dictionary_destroy(mowgli_dictionary_t *dtree, void (*destroy_cb)(mowgli_dictionary_elem_t *delem, void *privdata), void *privdata)

This function destroys all entries in the given dictionary.
If destroy_cb is defined, the passed function will be called
for each element in the dictionary. This function is used for
deleting the contents of the elements. The callback function
is passed both the elements and the data given in the privdata
argument.
