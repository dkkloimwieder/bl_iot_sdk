#
# This is a project Makefile. It is assumed the directory this Makefile resides in is a
# project subdirectory.
#

PROJECT_NAME := demo_os
PROJECT_PATH := $(abspath .)
PROJECT_BOARD := evb
export PROJECT_PATH PROJECT_BOARD
#CONFIG_TOOLPREFIX :=

-include ./proj_config.mk

ifeq ($(origin BL60X_SDK_PATH), undefined)
BL60X_SDK_PATH_GUESS ?= $(shell pwd)
BL60X_SDK_PATH ?= $(BL60X_SDK_PATH_GUESS)/../../../..
$(info ****** Please SET BL60X_SDK_PATH ******)
$(info ****** Trying SDK PATH [$(BL60X_SDK_PATH)])
endif

ifeq ("$(CONFIG_CHIP_NAME)", "BL606p")
COMPONENTS_BLSYS   := 
COMPONENTS_VFS     := 

INCLUDE_COMPONENTS += bl606p_e906_freertos_ram bl606p bl606p_std newlibc hosal vfs utils yloop cli blog
INCLUDE_COMPONENTS += 
endif

ifeq ("$(CONFIG_CHIP_NAME)", "BL616")
COMPONENTS_BLSYS   := 
COMPONENTS_VFS     := 

INCLUDE_COMPONENTS += bl616_e907_freertos_ram bl616_std bl616 hosal vfs utils yloop cli blog blfdt hosal
endif

ifeq ("$(CONFIG_CHIP_NAME)", "BL602")
COMPONENTS_BLSYS   := bltime blfdt blmtd bloop loopadc looprt loopset
COMPONENTS_VFS     := romfs

INCLUDE_COMPONENTS += freertos_riscv_ram bl602 bl602_std newlibc hosal vfs yloop utils cli blog blog_testc
INCLUDE_COMPONENTS += easyflash4 coredump
endif

INCLUDE_COMPONENTS += $(COMPONENTS_BLSYS)
INCLUDE_COMPONENTS += $(COMPONENTS_VFS)

INCLUDE_COMPONENTS += $(PROJECT_NAME)

include $(BL60X_SDK_PATH)/make_scripts_riscv/project.mk
