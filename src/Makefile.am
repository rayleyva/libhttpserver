#
#     This file is part of libhttpserver
#     Copyright (C) 2011, 2012, 2013, 2014, 2015 Sebastiano Merlino
#
#     This library is free software; you can redistribute it and/or
#     modify it under the terms of the GNU Lesser General Public
#     License as published by the Free Software Foundation; either
#     version 2.1 of the License, or (at your option) any later version.
#
#     This library is distributed in the hope that it will be useful,
#     but WITHOUT ANY WARRANTY; without even the implied warranty of
#     MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
#     Lesser General Public License for more details.
#
#     You should have received a copy of the GNU Lesser General Public
#     License along with this library; if not, write to the Free Software
#     Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA

AM_CPPFLAGS = -I../ -I$(srcdir)/httpserver/
METASOURCES = AUTO
lib_LTLIBRARIES = libhttpserver.la
libhttpserver_la_SOURCES = string_utilities.cpp webserver.cpp http_utils.cpp http_request.cpp http_response.cpp http_resource.cpp details/comet_manager.cpp http_endpoint.cpp
noinst_HEADERS = httpserver/string_utilities.hpp httpserver/details/modded_request.hpp httpserver/details/http_response_ptr.hpp httpserver/details/cache_entry.hpp httpserver/details/comet_manager.hpp gettext.h
nobase_include_HEADERS = httpserver.hpp httpserver/create_webserver.hpp httpserver/webserver.hpp httpserver/http_utils.hpp httpserver/http_endpoint.hpp httpserver/http_request.hpp httpserver/http_response.hpp httpserver/http_resource.hpp httpserver/binders.hpp httpserver/http_response_builder.hpp

AM_CXXFLAGS += -fPIC -Wall

if COND_GCOV
AM_CFLAGS += -O0 --coverage --no-inline
AM_CXXFLAGS += -O0 --coverage --no-inline
AM_LDFLAGS += -O0 --coverage -lgcov --no-inline
endif

libhttpserver_la_LIBADD = -lmicrohttpd
libhttpserver_la_CFLAGS = $(AM_CFLAGS)
libhttpserver_la_CXXFLAGS = $(AM_CXXFLAGS)
libhttpserver_la_LDFLAGS = $(AM_LDFLAGS) -no-undefined

install-data-hook:
	(mkdir -p $(DESTDIR)$(includedir) && cd $(DESTDIR)$(includedir) && $(LN_S) -f httpserver.hpp httpserverpp)

uninstall-hook:
	(cd $(DESTDIR)$(includedir) && rm -f httpserverpp)
