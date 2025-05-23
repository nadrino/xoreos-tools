# xoreos-tools - Tools to help with xoreos development
#
# xoreos-tools is the legal property of its developers, whose names
# can be found in the AUTHORS file distributed with this source
# distribution.
#
# xoreos-tools is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 3
# of the License, or (at your option) any later version.
#
# xoreos-tools is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with xoreos-tools. If not, see <http://www.gnu.org/licenses/>.

# The main "controller" automake recipe. We're setting up all our
# global build variables here, then recursively include all other
# build recipe, creating a flat non-recursive automake setup.

# Use the m4 directory for extra m4 autoconf scripts.
ACLOCAL_AMFLAGS = -I m4 --install

# Empty element to make the source lists easier editable.
EMPTY =

# Initialize the global lists.

noinst_HEADERS     =
noinst_LTLIBRARIES =

bin_PROGRAMS =

check_LTLIBRARIES =
check_PROGRAMS    =
TESTS             =

CLEANFILES =

EXTRA_DIST     =
dist_doc_DATA  =
dist_man1_MANS =

# Library compile flags

LIBSF_XOREOS  = $(XOREOSTOOLS_CFLAGS)
LIBSF_GENERAL = $(ZLIB_CFLAGS) $(LZMA_FLAGS) $(XML2_CFLAGS)
LIBSF_BOOST   = $(BOOST_CPPFLAGS)

LIBSF         = $(LIBSF_XOREOS) $(LIBSF_GENERAL) $(LIBSF_BOOST)

# Library linking flags

LIBSL_XOREOS  = $(XOREOSTOOLS_LIBS)
LIBSL_GENERAL = $(LTLIBICONV) $(ZLIB_LIBS) $(LZMA_LIBS) $(XML2_LIBS)
LIBSL_BOOST   = $(BOOST_SYSTEM_LDFLAGS) $(BOOST_SYSTEM_LIBS) \
                $(BOOST_FILESYSTEM_LDFLAGS) $(BOOST_FILESYSTEM_LIBS) \
                $(BOOST_LOCALE_LDFLAGS) $(BOOST_LOCALE_LIBS)

LIBSL         = $(LIBSL_XOREOS) $(LIBSL_GENERAL) $(LIBSL_BOOST)

# Other compiler flags

FLAGS_DIR     = -I$(srcdir)
FLAGS_DEBUG   = $(GGDB)
FLAGS_STD     = $(STD)
FLAGS_OPT     = $(LTO) $(NATIVE)
FLAGS_WARN    = $(WARN) $(WERROR)

FLAGS         = $(FLAGS_DIR) $(FLAGS_DEBUG) $(FLAGS_STD) \
                $(FLAGS_OPT) $(FLAGS_WARN)

# Putting it all together...

AM_CXXFLAGS   = $(FLAGS) $(LIBSF)
AM_LDFLAGS    = $(FLAGS_OPT)
LDADD         = $(LIBSL)
LIBS          =

# Now include the top-level recipe file and through it, all the
# other build recipes.

include rules.mk
