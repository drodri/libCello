IF(MSVC)
	MESSAGE(FATAL_ERROR "Libcello not supported in Visual")
ENDIF()

ADD_BIICODE_TARGETS()

# Extra configuration
TARGET_COMPILE_OPTIONS(${BII_BLOCK_TARGET} INTERFACE "-std=gnu99")
if(EXISTS ${CMAKE_CURRENT_BINARY_DIR}/cmake_dummy.cpp)
	set_source_files_properties(${CMAKE_CURRENT_BINARY_DIR}/cmake_dummy.cpp PROPERTIES COMPILE_FLAGS -std=c++03)
endif()
IF(UNIX)
	TARGET_LINK_LIBRARIES(${BII_BLOCK_TARGET} INTERFACE -lpthread -ldl -lm)
ENDIF()
