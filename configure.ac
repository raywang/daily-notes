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
AC_CHECK_PROG(HAVE_PKGCONFIG, pkg-config, yes, no)
if test "x$HAVE_PKGCONFIG" = "xno"; then
	  AC_MSG_ERROR(you need to have pkgconfig installed !)
fi

####################
# i18n
####################
GETTEXT_PACKAGE=daily-notes
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE", [Gettext package])

####################
# Python
####################
AM_PATH_PYTHON(2.4)

# pygtk deps
AC_MSG_CHECKING(for pygtk defs)
PYGTK_DEFSDIR=`pkg-config --variable=defsdir pygtk-2.0`
AC_SUBST(PYGTK_DEFSDIR)
AC_MSG_RESULT($PYGTK_DEFSDIR)

# sqlite3 deps
AC_MSG_CHECKING([for python sqlite module])
    if AC_RUN_LOG([DISPLAY= $PYTHON -c '
try:
    import sqlite3
except ImportError, e:
    if str(e).find("sqlite3") >= 0:
        raise
except:
    pass
    ']); then
      AC_MSG_RESULT([yes])
    else
      AC_MSG_RESULT([no])
      AC_MSG_ERROR([Python 2.5+: inbuilt sqlite is required to build daily-notes])
    fi

# gettext deps
AC_MSG_CHECKING([for python gettext module])
    if AC_RUN_LOG([DISPLAY= $PYTHON -c '
try:
    import gettext
except ImportError, e:
    if str(e).find("gettext") >= 0:
        raise
except:
    pass
    ']); then
      AC_MSG_RESULT([yes])
    else
      AC_MSG_RESULT([no])
      AC_MSG_ERROR([Python 2.5+: inbuilt gettext is required to build daily-notes])
    fi

# dbus deps
AC_MSG_CHECKING([for python dbus module])
    if AC_RUN_LOG([DISPLAY= $PYTHON -c '
try:
    import dbus
except ImportError, e:
    if str(e).find("dbus") >= 0:
        raise
except:
    pass
    ']); then
      AC_MSG_RESULT([yes])
    else
      AC_MSG_RESULT([no])
      AC_MSG_ERROR([Python 2.5+: dbus is required to build daily-notes])
    fi

####################
# Output
####################
AC_CONFIG_SRCDIR(src/daily-notes.in)
AC_CONFIG_FILES([Makefile
                 src/daily-notes
                 src/Makefile
                 data/Makefile
                 po/Makefile.in])

AC_OUTPUT
