#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.61])
AC_INIT([pylibacl], [0.4.0], [https://github.com/iustin/pylibacl/issues])
AC_CONFIG_SRCDIR([acl.c])
AC_CONFIG_HEADER([config.h])
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE([foreign])
AM_MAINTAINER_MODE

# Checks for programs.
AC_PROG_CC

# Checks for libraries.
gl_FUNC_ACL

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_TYPE_MODE_T
AC_TYPE_SSIZE_T
AC_TYPE_UID_T

# Checks for library functions.

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
