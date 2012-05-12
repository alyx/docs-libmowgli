mowgli.hook
===========

.. c:type:: mowgli_hook_function_t

This type is a typedef of void, set as a function which accepts
two parameters. The first, hook_data, is a void pointer to a block
of memory containing data sent to the function called by the hook.
The second, user_data, is another void pointer to a block of memory
containing a specific set of data specified at hook creation time, which
is sent back to the hook method on each call.

.. c:function:: mowgli_hook_bootstrap(void)

This function bootstraps (initialises) the hook system, initialising
the patricia trie used to keep a record of the existing hooks and
allocating memory to the heap which new hooks draw memory from when created.

.. c:function:: mowgli_hook_register(const char *name)

This function registers a new hook with the hook system.
It accepts one parameter, a string containing the name of the hook.

.. c:function:: mowgli_hook_associate(const char *name, mowgli_hook_function_t func, void *user_data)

This function associates a function with the specified hook. If a hook of the
specified name does not exist, this function will call
:c:func:`mowgli_hook_register()` and create the needed hook.

It accepts three parameters, a string containing the hook name, a
:c:type:`mowgli_hook_function_t` object pointing to the callback function, and
a void pointer to the user data sent to the callback on each call.
This function will return -1 on error or 0 if no errors occur.

.. c:function:: mowgli_hook_dissociate(const char *name, mowgli_hook_function_t func)

This function dissociates a function from the specified hook. It accepts
two parameters, a string containing the hook to remove the function from
and the :c:type:`mowgli_hook_function_t` pointer to the function itself.
This function will return -1 on error or 0 if no errors occur.

.. c:function:: void mowgli_hook_call(const char *name, void *hook_data)

This function will call all callback methods registered for the specified hook,
sending each of them the data pointed to by hook_data.

This function accepts two parameters, a string containing the name of the hook
to be called and a void pointer to the memory containing the data needing to be
sent to the hook callbacks.
