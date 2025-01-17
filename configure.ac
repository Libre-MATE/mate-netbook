#   Copyright (C) 2022  Libre MATE
#
# This file is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; see the file COPYING3.  If not see
# <http://www.gnu.org/licenses/>.

AC_INIT([mate-netbook],
        [1.26.0],
        [https://github.com/Libre-MATE/mate-netbook/issues],
        [mate-netbook],
        [https://github.com/Libre-MATE/mate-netbook/])
AC_PREREQ(2.60)
AC_COPYRIGHT([Copyright (C) 2022 Libre MATE])
AM_INIT_AUTOMAKE([1.11 foreign tar-ustar no-dist-gzip dist-xz check-news])
AM_SILENT_RULES([yes])
AC_CONFIG_SRCDIR(maximus/main.c)
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_HEADERS([config.h])
AM_MAINTAINER_MODE

MATE_COMPILE_WARNINGS

AC_PROG_CC
AC_PROG_SED
LT_INIT

dnl ==========================================================================
dnl i18n
dnl ==========================================================================
AM_GNU_GETTEXT_VERSION([0.19.8])
AM_GNU_GETTEXT([external])

GETTEXT_PACKAGE=AC_PACKAGE_NAME
AC_SUBST(GETTEXT_PACKAGE)
AC_SUBST([CONFIG_STATUS_DEPENDENCIES],['$(top_srcdir)/po/LINGUAS'])
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE", [Define to the Gettext package name])

AC_SUBST(GCC_FLAGS)

GLIB_REQUIRED=2.50.0
GTK_REQUIRED=3.22.0

PKG_CHECK_MODULES(MAXIMUS_DEPS,
                  gtk+-3.0 >= $GTK_REQUIRED
                  glib-2.0 >= $GLIB_REQUIRED
                  gio-2.0
                  libwnck-3.0
                  xtst
                  libfakekey
                  )
AC_SUBST(MAXIMUS_DEPS_CFLAGS)
AC_SUBST(MAXIMUS_DEPS_LIBS)

PKG_CHECK_MODULES(MATEWINDOWPICKER_DEPS,
                  libmatepanelapplet-4.0 >= 1.17.0
                  gtk+-3.0 >= $GTK_REQUIRED
                  glib-2.0 >= $GLIB_REQUIRED
                  gio-2.0
                  libwnck-3.0
                  )
AC_SUBST(MATEWINDOWPICKER_DEPS_CFLAGS)
AC_SUBST(MATEWINDOWPICKER_DEPS_LIBS)

GLIB_GSETTINGS

AC_CONFIG_FILES([
Makefile
maximus/Makefile
maximus/org.mate.maximus.gschema.xml
mate-window-picker-applet/Makefile
mate-window-picker-applet/org.mate.panel.applet.mate-window-picker-applet.gschema.xml
po/Makefile.in
])
AC_OUTPUT

dnl ---------------------------------------------------------------------------
dnl - Show summary
dnl ---------------------------------------------------------------------------

echo "
       mate-netbook $VERSION
       `echo mate-netbook $VERSION | sed "s/./=/g"`

       prefix:                        ${prefix}
       compiler:                      ${CC}
       cflags:                        ${CFLAGS}
       warning flags:                 ${WARN_CFLAGS}
"
