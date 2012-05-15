mowgli.signal
=============

.. c:function:: mowgli_signal_handler_t mowgli_signal_install_handler(int signum, mowgli_signal_handler_t handler)

This function is a version of signal(2) intended to work more reliably across
different platforms.

It restarts interrupted system calls, does not reset the handler and blocks
the same signal from within the handler.

This function accepts two parameters, an integer specifying which signal to
install the handler for and a function pointing to the signal handler.

On success, this function returns a pointer to the handler. On failure, this
function returns NULL.

.. c:type:: mowgli_signal_handler_t

This type is a typedef of a void function pointer which accepts
an integer as the argument.
