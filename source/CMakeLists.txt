set( CMAKE_CXX_STANDARD 17 )
set( CMAKE_CXX_STANDARD_REQUIRED ON )
set( CMAKE_CXX_EXTENSIONS OFF )

add_library( ${SON8_LIB} STATIC )
target_sources( ${SON8_LIB} PRIVATE
    windowed.cxx
)

target_link_libraries( ${SON8_LIB} PRIVATE glfw::son8 )

if( NOT TARGET son8__overglad )
    include( FetchContent )
    message( STATUS "${SON8_LIB}: FetchContent `soneight/overglad`" )
    FetchContent_Declare(
        son8__overglad
        GIT_REPOSITORY https://github.com/soneight/overglad.git
        GIT_TAG        81e45016b5955d9150737fe252b53250c6d5aff2 # v0.0.8
    )
    FetchContent_MakeAvailable( son8__overglad )
endif( )
message( STATUS "${SON8_LIB}: target `son8__overglad` found" )

# Apache License 2.0
# NO WARRANTY OF ANY KIND see <http://www.apache.org/licenses/LICENSE-2.0>
# SPDX-License-Identifier: Apache-2.0
# lib: `windowed` C++17 Overglad GLFW Based Window
# Ⓒ Copyright (c) 2025-2026 Oleg'Ease'Kharchuk ᦒ
