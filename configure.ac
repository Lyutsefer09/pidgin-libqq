# Copyright (C) 2008 Alexander Logvinov <ports@logvinov.com> 
# Copyright (C) 2011 microcai <microcaicai@gmail.com>
# Copyright (C) 2012 cnangel <cnangel@gmail.com>
#   
# This file is free software; as a special exception the author gives 
# unlimited permission to copy and/or distribute it, with or without  
# modifications, as long as this notice is preserved. 
#  
# This program is distributed in the hope that it will be useful, but 
# WITHOUT ANY WARRANTY, to the extent permitted by law; without even the 
# implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. 

AC_INIT([pidgin-libqq],[0.72],[http://code.google.com/p/libqq-pidgin/issues/list])
#AM_CONFIG_HEADER([config.h])
AM_INIT_AUTOMAKE([-Wall])
AC_CONFIG_MACRO_DIR([m4])
#AC_CONFIG_HEADERS([config.h])

PACKAGE_RELEASE=1
BITS=`if [[ 64 -eq $(getconf LONG_BIT) ]]; then echo -n $(getconf LONG_BIT); fi`
PACKAGE_URL=https://github.com/cnangel/pidgin-libqq
DOXYGEN_OUTPUT_DIR=doc/doxygen

AC_SUBST(PACKAGE_RELEASE)
AC_SUBST(BITS)
AC_SUBST(PACKAGE_URL)
AC_SUBST(DOXYGEN_OUTPUT_DIR)

AC_PROG_CC
AM_DISABLE_STATIC
AC_LIBTOOL_DLOPEN
AC_PROG_LIBTOOL

# Check for pkg-config
PKG_PROG_PKG_CONFIG

PKG_CHECK_MODULES([PURPLE],[purple >= 2.7.0 ],,AC_MSG_ERROR([
*** libpurple 2.0+ >=2.7.0  is required to build.]))
AC_SUBST(PURPLE_CFLAGS)
AC_SUBST(PURPLE_LIBS)
PURPLE_LIBDIR=$(pkg-config --variable=libdir purple)
PURPLE_DATADIR=$(pkg-config --variable=datadir purple)
PURPLE_PLUGINDIR=$(pkg-config --variable=plugindir purple)
AC_SUBST(PURPLE_LIBDIR)
AC_SUBST(PURPLE_DATADIR)
AC_SUBST(PURPLE_PLUGINDIR)
datadir=${PURPLE_DATADIR}
pluginsdir=${PURPLE_PLUGINDIR}
AC_SUBST(pluginsdir)

PKG_CHECK_MODULES([GLIB],[glib-2.0])

AM_CONDITIONAL([STATIC_QQ],[false])
AC_OUTPUT([Doxyfile Makefile tools/Makefile pidgin-libqq.spec pixmaps/Makefile])
