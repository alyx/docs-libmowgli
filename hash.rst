mowgli.hash
===========

mowgli.hash is a portable implementation of the FNV-1 hash.

.. c:function:: int mowgli_fnv_hash_string(const char *p)

This function accepts a string and returns an integer containing
the hashed value of said string.

.. c:function:: int mowgli_fnv_hash(unsigned int *p)

This function accepts a pointer to an unsigned integer and returns
an integer containing the hashed value of the input.
