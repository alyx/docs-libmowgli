mowgli.assert
=============

.. c:macro:: soft_assert(x)

This macro evaluates a function, x. Upon error (The function 
evaluating as false), this macro will call 
:c:func:`mowgli_soft_assert_log`, logging the function evaluated,
the file it was called from, and the specific line in said file.

.. c:macro:: return_if_fail(x)

This macro, like :c:macro:`soft_assert`, evaluates function x and logs
to :c:func:`mowgli_soft_assert_log` on failure. This function will also
return on assertion fail.

.. c:macro:: return_val_if_fail(x, y)

This macro is the same as :c:macro:`return_if_fail`, with the addition that
in the case of function x failing, value y will be returned.

