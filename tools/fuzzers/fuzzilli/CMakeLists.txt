# Copyright (c) Meta Platforms, Inc. and affiliates.
#
# This source code is licensed under the MIT license found in the
# LICENSE file in the root directory of this source tree.

if(HERMES_ENABLE_FUZZILLI)
    set(HERMES_ENABLE_EH_RTTI ON)
    set(HERMES_ENABLE_FUZZILLI ON)

    add_hermes_tool(fuzzilli
      fuzzilli.cpp
      ${ALL_HEADER_FILES}
    )

    target_include_directories(fuzzilli PRIVATE ${HERMES_SOURCE_DIR}/API)
    target_compile_options(fuzzilli PRIVATE -fsanitize-coverage=trace-pc-guard)
    target_link_libraries(fuzzilli libhermes)
endif()
