#
#  openvpnmsica -- Custom Action DLL to provide OpenVPN-specific support to MSI packages
#
#  Copyright (C) 2002-2025 OpenVPN Inc <sales@openvpn.net>
#  Copyright (C) 2018-2025 Simon Rozman <simon@rozman.si>
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License version 2
#  as published by the Free Software Foundation.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License along
#  with this program; if not, write to the Free Software Foundation, Inc.,
#  51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
#

include $(top_srcdir)/ltrc.inc

MAINTAINERCLEANFILES = $(srcdir)/Makefile.in

AM_CPPFLAGS = \
	-I$(top_srcdir)/include -I$(top_srcdir)/src/compat

AM_CFLAGS = \
	$(TAP_CFLAGS)

EXTRA_DIST = \
	CMakeLists.txt

if WIN32
lib_LTLIBRARIES = libopenvpnmsica.la
libopenvpnmsica_la_CFLAGS = \
	-municode -D_UNICODE \
	-UNTDDI_VERSION -U_WIN32_WINNT \
	-D_WIN32_WINNT=_WIN32_WINNT_VISTA \
	-Wl,--kill-at
libopenvpnmsica_la_LDFLAGS = -ladvapi32 -lole32 -lmsi -lsetupapi -liphlpapi -lshell32 -lshlwapi -lversion -lnewdev -no-undefined -avoid-version
endif

libopenvpnmsica_la_SOURCES = \
	dllmain.c \
	msiex.c msiex.h \
	msica_arg.c msica_arg.h \
	openvpnmsica.c openvpnmsica.h \
	$(top_srcdir)/src/tapctl/basic.h \
	$(top_srcdir)/src/tapctl/error.c $(top_srcdir)/src/tapctl/error.h \
	$(top_srcdir)/src/tapctl/tap.c $(top_srcdir)/src/tapctl/tap.h \
	openvpnmsica_resources.rc
