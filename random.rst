mowgli.random
=============

.. c:function:: void mowgli_random_bootstrap(void)

This function initialises mowgli.random.

.. c:function:: mowgli_random_t *mowgli_random_create(void)

This function creates a new :c:type:`mowgli_random_t` object using the
current time as the seed.

.. c:function:: mowgli_random_t mowgli_random_create_with_seed(unsigned int seed)

This function creates a new :c:type:`mowgli_random_t` object, seeded with the
integer supplied in "seed."

.. c:function:: void mowgli_random_reseed(mowgli_random_t *self, unsigned int seed)

This function reseeds the :c:type:`mowgli_random_t` object "self" using
the integer supplied in "seed."

.. c:function:: unsigned int mowgli_random_int(mowgli_random_t *self)

This function generates a random unsigned integer using 
the seed from :c:type:`mowgli_random_t` object "self."

.. c:function:: int mowgli_random_int_ranged(mowgli_random_t *self, int begin, int end)

This function generates a random integer from "self" between the values
"begin" and "end."

.. c:type:: mowgli_random_t

This type is a typedef of a structure containing the state of the object.
