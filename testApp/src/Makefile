TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#=============================

#=============================
# Build the IOC application
#

PROD_IOC = pydevioc
# pydevioc.dbd will be created and installed
DBD += pydevioc.dbd

# pydev.dbd will be made up from these files:
pydevioc_DBD += base.dbd
pydevioc_DBD += pydev.dbd

# Include dbd files from all support applications:
#pydevioc_DBD += xxx.dbd

# Add all the support libraries needed by this IOC
pydevioc_LIBS += pydev

# pydevioc_registerRecordDeviceDriver.cpp derives from pydev.dbd
pydevioc_SRCS += pydevioc_registerRecordDeviceDriver.cpp

# Build the main IOC entry point on workstation OSs.
pydevioc_SRCS_DEFAULT += main.cpp
pydevioc_SRCS_vxWorks += -nil-

# Add support from base/src/vxWorks if needed
#pydevioc_OBJS_vxWorks += $(EPICS_BASE_BIN)/vxComLibrary

# Finally link to the EPICS Base libraries
pydevioc_LIBS += $(EPICS_BASE_IOC_LIBS)
# Starting with Python 3.8, python-config needs --embed flag
PYTHON_EMBED := $(shell $(PYTHON_CONFIG) --help | grep embed)
ifeq ($(PYTHON_EMBED),)
	SYS_PROD_LIBS += $(shell $(PYTHON_CONFIG) --ldflags | sed 's/-[^l][^ ]*//g' | sed 's/-l//g')
else
	SYS_PROD_LIBS += $(shell $(PYTHON_CONFIG) --ldflags --embed | sed 's/-[^l][^ ]*//g' | sed 's/-l//g')
endif

#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

