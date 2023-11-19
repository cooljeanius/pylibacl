dnl#                                               -*- Autoconf -*-
dnl# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.70])dnl
AC_INIT([pylibacl],[0.5.3],[https://github.com/iustin/pylibacl/issues])dnl
AC_CONFIG_SRCDIR([acl.c])dnl
AC_CONFIG_HEADERS([config.h])dnl
AC_CONFIG_MACRO_DIR([m4])dnl
AC_CONFIG_AUX_DIR([build-aux])dnl
AC_REQUIRE_AUX_FILE([compile])dnl
AC_REQUIRE_AUX_FILE([depcomp])dnl
AC_REQUIRE_AUX_FILE([missing])dnl
AC_CANONICAL_TARGET
AM_INIT_AUTOMAKE([foreign])dnl
AM_MAINTAINER_MODE
AC_EXEEXT
AC_USE_SYSTEM_EXTENSIONS
AC_SEARCH_LIBS([strerror],[cposix])dnl

# Checks for programs.
AM_PROG_AR
AM_PROG_CC_C_O
AC_PROG_GCC_TRADITIONAL
AM_PATH_PYTHON([2.4])
AC_SUBST([PYTHON])dnl
AC_PATH_PROG([FAKEROOT],[fakeroot],[fakeroot])dnl
AC_PATH_PROG([SPHINX_BUILD],[sphinx-build],[sphinx-build])dnl
AC_SUBST([SPHINX_BUILD])dnl
AC_PATH_PROG([CHMOD],[chmod])dnl

# Next two lines is a hack to prevent libtool checking for CXX/F77
define([AC_LIBTOOL_LANG_CXX_CONFIG],[:])dnl
define([AC_LIBTOOL_LANG_F77_CONFIG],[:])dnl
LT_INIT
LT_LANG([C])dnl
LT_SYS_MODULE_EXT
AC_SUBST([LT_MODULE_EXT])dnl
AC_SUBST([LT_SHARED_EXT])dnl

gl_LDD

AC_BAKEFILE_GNUMAKE
AC_BAKEFILE_SUFFIXES
AC_BAKEFILE_SHARED_VERSIONS

XORG_LD_WRAP
XORG_MEMORY_CHECK_FLAGS

# Checks for libraries.
AC_CHECK_LIB([c],[main])
WINE_CHECK_SONAME([c],[main])
gl_FUNC_ACL

AC_SUBST([SO_SUFFIX])dnl

# Checks for header files.
AC_CHECK_HEADERS([acl.h stdio.h Python.h Python/Python.h])dnl

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_TYPE_MODE_T
AC_TYPE_SSIZE_T
AC_TYPE_UID_T
AC_CHECK_DECLS([ACL_READ, ACL_WRITE],[],[],[
#ifdef HAVE_ACL_H
# include <acl.h>
#else
# ifdef HAVE_SYS_ACL_H
#  include <sys/acl.h>
# else
#  ifdef HAVE_ACL_LIBACL_H
#   include <acl/libacl.h>
#  else
#   if defined(__GNUC__) && !defined(__STRICT_ANSI__)
#    warning "conftest for acl decls needs an acl-related header"
#   endif /* __GNUC__ && !__STRICT_ANSI__ */
#  endif /* HAVE_ACL_LIBACL_H */
# endif /* HAVE_SYS_ACL_H */
#endif /* HAVE_ACL_H */
])dnl

# Checks for library functions.
# This first set should exist on Darwin:
AC_CHECK_FUNCS([acl_add_perm acl_clear_perms acl_copy_entry \
acl_create_entry acl_delete_entry acl_delete_perm acl_dup \
acl_get acl_get_permset acl_get_qualifier acl_get_tag_type \
acl_init acl_set acl_set_permset acl_set_qualifier acl_set_tag_type \
acl_to_text acl_valid posix1e])
# This second set is unsupported on Darwin:
AC_CHECK_FUNCS([acl_calc_mask])dnl

# Output.
AC_CONFIG_FILES([Makefile])
AC_OUTPUT
