# Makefile
TOP = ../..
include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE

USR_LDFLAGS += $(shell $(PYTHON_CONFIG) --ldflags)
USR_CXXFLAGS += $(subst -Wstrict-prototypes,,$(shell $(PYTHON_CONFIG) --cflags))
USR_CXXFLAGS += -I$(TOP)/src
USR_CXXFLAGS += -std=c++11 -g -ggdb -O0
SRC_DIRS += ../..

PROD_LIBS = Com

TESTPROD_HOST = testutil
testutil_SRCS += test_util.cpp
testutil_SRCS += util.cpp
TESTS += testutil

TESTSCRIPTS_HOST = $(TESTS:%=%.t)

include $(TOP)/configure/RULES

