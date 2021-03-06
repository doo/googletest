AC_INIT([Google C++ Testing Framework],
        [1.0.1],
        [googletestframework@googlegroups.com],
        [gtest])

# Provide various options to initialize the Autoconf and configure processes.
AC_PREREQ([2.59])
AC_CONFIG_SRCDIR([./COPYING])
AC_CONFIG_AUX_DIR([config_aux])
AC_CONFIG_HEADERS([config_aux/config.h])
AC_CONFIG_FILES([Makefile])
AC_CONFIG_FILES([scripts/gtest-config], [chmod +x scripts/gtest-config])

# Initialize Automake with various options. We require at least v1.9, prevent
# pedantic complaints about package files, and enable various distribution
# targets.
AM_INIT_AUTOMAKE([1.9 dist-bzip2 dist-zip foreign subdir-objects])

# Check for programs used in building Google Test.
AC_PROG_CC
AC_PROG_CXX
AC_LANG([C++])
AC_PROG_LIBTOOL

# TODO(chandlerc@google.com): Currently we aren't running the Python tests
# against the interpreter detected by AM_PATH_PYTHON, and so we condition
# HAVE_PYTHON by requiring "python" to be in the PATH, and that interpreter's
# version to be >= 2.4. This will allow the scripts to use a "/usr/bin/env"
# hashbang.
#AM_PATH_PYTHON([2.4],,[:])
PYTHON=  # We *do not* allow the user to specify a python interpreter
AC_PATH_PROG([PYTHON],[python],[:])
AS_IF([test "$PYTHON" != ":"],
      [AM_PYTHON_CHECK_VERSION([$PYTHON],[2.4],[:],[PYTHON=":"])])
AM_CONDITIONAL([HAVE_PYTHON],[test "$PYTHON" != ":"])

# TODO(chandlerc@google.com) Check for the necessary system headers.

# TODO(chandlerc@google.com) Check the types, structures, and other compiler
# and architecture characteristics.

# Output the generated files. No further autoconf macros may be used.
AC_OUTPUT
