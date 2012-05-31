mowgli.module
=============

These functions are for the cross-platform loading of dynamicly loaded modules.

.. c:function:: mowgli_module_t mowgli_module_open(const char *path)

This function accepts a filename, specifying the path of the module to load.
It then attempts to load said module (using dlopen on POSIX platforms and LoadLibraryA on Windows)
and return a :c:type:`mowgli_module_t` handle to the module. On failure, it returns NULL.

.. c:function:: void * mowgli_module_symbol(mowgli_module_t module, const char *symbol)

This function attempts to find a specific symbol within the given module.
On success, it returns a pointer to the symbol; on failure, this function returns NULL.

.. c:function:: void mowgli_module_close(mowgli_module_t module)

This function closes the specified module.

.. c:type:: mowgli_module_t

This type is a typedef of void. On Windows, HANDLE is cast as a mowgli_module_t.
