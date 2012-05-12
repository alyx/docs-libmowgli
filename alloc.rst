mowgli.alloc
============

Libmowgli provides a series of allocation methods designed to be a safe,
portable wrapper around malloc, calloc, and free.

.. c:function:: void * mowgli_alloc_array_using_policy(mowgli_allocation_policy_t *policy, size_t size, size_t count) 

This function allocates an array of data that contains "count" objects
of "size" size. This function usually wraps calloc(), however the specific
allocation policy used may have a different allocator.

It accepts three parameters. The policy struct, a size_t value stating the size
of the objects, and a count of the amount of objects to be allocated to the array.
It returns a pointer to the allocated memory buffer.

.. c:function:: void * mowgli_alloc_using_policy(mowgli_allocation_policy_t *policy, size_t size)

This function is the equivilant of calling mowgli_alloc_array(size, 1).

It accepts two parameters, the allocation policy and the size of the object
to allocate.
It returns a pointer to the allocated memory buffer.

.. c:function:: char * mowgli_strdup_using_policy(mowgli_allocation_policy_t *policy, const char *in)

This function will duplicate a string via mowgli_alloc() using the specified policy.

It accepts two parameters, the allocation policy and the string to duplicate.
This function will return a pointer to the duplicated string.

.. c:function:: char * mowgli_strdup(const char *in)

This function calls :c:func:`mowgli_strdup_using_policy()` using the default
allocation policy.

It accepts one parameter, the string to duplicate.
This function will return a pointer to the duplicated string.

.. c:function:: char * mowgli_strndup_using_policy(mowgli_allocation_policy_t *policy, const char *in, size_t size)

This function will duplicate a string of "size" length via mowgli_alloc()
using the specified policy.

It accepts three parameters, the allocation policy, the string to duplicate,
and the length of the final string (How much of the original to duplicate).
This function will return a pointer to the duplicated string.

.. c:function:: char * mowgli_strndup(const char *in, size_t size)

This function calls :c:func:`mowgli_strndup_using_policy()` using the default
allocation policy.

It accepts two parameters, the string to duplicate and the amount to be
duplicated.
This function will return a pointer to the duplicated string.

.. c:function:: void * mowgli_alloc_array(size_t size, size_t count)

This function allocates an array of data that contains "count" objects of
"size" size using the default allocation policy.

It accepts two parameters, the size of the object to allocate and the
amount of objects.
This function will return a pointer to the allocated memory buffer.

.. c:function:: void * mowgli_alloc(size_t size)

This function allocates an object of "size" size. This is the
equivilant of calling mowgli_alloc_array(size, 1). 

This function accepts one parameter, a size_t value containing the size of the 
amount of memory wished to be allocated. 
It returns a pointer to the allocated memory buffer.

.. c:function:: void mowgli_free(void *ptr)

This function frees an object back to the system memory pool.
It wraps free() to protect against common mistakes, which are
instead reported as errors.

This function accepts one parameter, a pointer to
the object to be freed. 

.. c:function:: void mowgli_allocator_set_policy(mowgli_allocation_policy_t *policy)

This function sets the default allocation policy used
by the allocation primitives.

It accepts one parameter, the allocation policy to use.

.. c:function:: void mowgli_allocator_set_policy_by_name(const char *name)

This function sets the default allocation policy to the policy
specified by the given name.

It accepts one parameter, a string containing the name of
the policy to use.

.. c:type:: mowgli_allocation_func_t

This type is a typedef of void, set as a function which accepts
a single parameter, "size", of type size_t. This type exists for use
within :c:type:`mowgli_allocation_policy_t`, and represents the 
function used for allocation of memory.

.. c:type:: mowgli_deallocation_func_t

This type is a typedef of void, set as a function which accepts
a single parameter, "ptr", a void-typed pointer to a memory object.
This type exists for use within :c:type:`mowgli_allocation_policy_t`,
and represents the function used for the deallocation of memory.

.. c:type:: mowgli_allocation_policy_t

This type is a struct containing a :c:type:`mowgli_allocation_func_t` pointer
to the allocation function and a :c:type:`mowgli_deallocation_func_t`
pointerto the deallocation function. It is used within mowgli.alloc for
specifying to the various allocation primitives what functions to use for
allocation and freeing of system memory.

.. c:function:: mowgli_allocation_policy_t * mowgli_allocation_policy_create(const char *name, mowgli_allocation_func_t allocator, mowgli_deallocation_func_t deallocator)

This function creates a new allocation policy, stored as "name", using
the specified allocation and deallocation functions.

It accepts three parameters, a string specifying the name of the policy,
an allocation function and a deallocation function.
this function will return a pointer to the
generated :c:type:`mowgli_allocation_policy_t` object.

.. c:function:: mowgli_allocation_policy_t * mowgli_allocation_policy_lookup(const char *name)

This function searches the policy list for a policy of the specified name.

It accepts one parameter, a string containing the policy name, and returns
the :c:type:`mowgli_allocation_policy_t` object for said policy, or NULL if
the policy is not found.
