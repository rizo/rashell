### configure.ac -- Autoconf for Rashell

# Rashell (https://github.com/michipili/rashell)
# This file is part of Rashell
#
# Copyright © 2015 Michael Grünewald
#
# This file must be used under the terms of the CeCILL-B.
# This source file is licensed as described in the file COPYING, which
# you should have received as part of this distribution. The terms
# are also available at
# http://www.cecill.info/licences/Licence_CeCILL-B_V1-en.txt

AC_INIT([meta/rashell.in])
AC_CONFIG_MACRO_DIR([Library/Autoconf])
AC_NEED_OCAML
AC_NEED_FINDLIB
AC_WITH_OCAML_SITE_LIB
AC_NEED_FINDLIB_PKG([broken])
AC_NEED_FINDLIB_PKG([lwt.unix])
AC_NEED_FINDLIB_PKG([lwt.ppx])
AC_NEED_FINDLIB_PKG([mixture])
AC_NEED_FINDLIB_PKG([str])

AC_PATH_PROG_REQUIRE([AWK], [awk])
AC_PATH_PROG_REQUIRE([CP], [cp])
AC_PATH_PROG_REQUIRE([DF], [df])
AC_PATH_PROG_REQUIRE([DU], [du])
AC_PATH_PROG_REQUIRE([FIND], [find])
AC_PATH_PROG_REQUIRE([GREP], [grep])
AC_PATH_PROG_REQUIRE([ID], [id])
AC_PATH_PROG_REQUIRE([LN], [ln])
AC_PATH_PROG_REQUIRE([MKTEMP], [mktemp])
AC_PATH_PROG_REQUIRE([MV], [mv])
AC_PATH_PROG_REQUIRE([RM], [rm])
AC_PATH_PROG_REQUIRE([SED], [sed])


# Docker command line tool
#
#   Support of Docker using the command line tool.

AC_ARG_WITH([docker],
  [AS_HELP_STRING([--with-docker],
    [add Docker support through the command-line tool.])],
  [WITH_DOCKER=${with_docker}
    case $with_docker in
    no)
      WITH_DOCKER='no'
      DOCKER='/nonexistant'
      ;;
    yes)
      AC_PATH_PROG_REQUIRE([DOCKER], [docker])
      WITH_DOCKER='yes'
      AC_NEED_FINDLIB_PKG([atdgen])
      ;;
    *)
      DOCKER="${with_docker}"
      WITH_DOCKER='yes'
      AC_NEED_FINDLIB_PKG([atdgen])
      ;;
    esac;],
  [AC_PATH_PROG([DOCKER], [docker], [/nonexistant])
   AS_IF([test "${DOCKER}" = '/nonexistant'], [WITH_DOCKER='no'], [WITH_DOCKER='yes'])])
AC_SUBST([WITH_DOCKER])

AC_CONFIG_FILES([Makefile.config src/rashell_Configuration.ml])
AC_OUTPUT

### End of file `configure.ac'
