#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.63)
AC_INIT([daily-notes],[0.2.0],[raywang@gnome.org])
AM_INIT_AUTOMAKE([-Wall -Werror])

AC_CONFIG_HEADERS(config.h)
IT_PROG_INTLTOOL([0.40])

#####################
# Pkg-Config
#####################
#AC_CHECK_PROG(HAVE_PKGCONFIG, pkg-config, yes, no)
#if test "x$HAVE_PKGCONFIG" = "xno"; then
#	  AC_MSG_ERROR(you need to have pkgconfig installed !)
#fi


####################
# Python
####################
AM_PATH_PYTHON(2.4)
AM_CHECK_PYGTK(2.0,,[AC_MSG_ERROR(Could not find pygtk 2.0)])
AM_CHECK_PYMOD(gettext,,,[AC_MSG_ERROR(Could not find python module gettext)])
AM_CHECK_PYMOD(sqlite3,,,[AC_MSG_ERROR(Could not find python module gettext)])
AM_CHECK_PYMOD(dbus,,,[AC_MSG_ERROR(Could not find python module gettext)])

####################
# Output
####################
AC_CONFIG_FILES([Makefile
                 po/Makefile.in])

AC_OUTPUT
