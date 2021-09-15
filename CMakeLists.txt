#################################################################################
# Copyright (c) 2021, Savely Pototsky (SavaLione)
# All rights reserved.
#################################################################################
# Checking the minimum version
cmake_minimum_required (VERSION 3.13.1)

# Project name
set(TFD_PROJECT "tfd")
set(TFD_PROJECT_VERSION "3.8.8")

project(${TFD_PROJECT}
    VERSION ${TFD_PROJECT_VERSION}
    LANGUAGES C
)

#################################################################################
#                                     Options                                   #
#################################################################################
option(TFD_BUILD_STATIC "Build static library" OFF)

#################################################################################
#                                       NFD                                     #
#################################################################################

set(TFD_SRC
    src/tinyfiledialogs.c
)

if(NFD_BUILD_STATIC)
    add_library(${TFD_PROJECT} STATIC ${TFD_SRC})
else()
    add_library(${TFD_PROJECT} SHARED ${TFD_SRC})
endif()
target_include_directories(${TFD_PROJECT} PUBLIC ${PROJECT_SOURCE_DIR}/include)