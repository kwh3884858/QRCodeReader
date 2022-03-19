cmake_minimum_required(VERSION 3.13)
Project(QRCodeReader)
set(FLAGS "-DUNICODE" "-D_UNICODE")

add_subdirectory(${PROJECT_SOURCE_DIR}/Library/zxing-cpp)
# target_link_libraries(zxing-cpp)
IF (WIN32)
    message(STATUS "current Platform: win32 ")
    add_executable(${PROJECT_NAME} WIN32)
    target_link_libraries(${PROJECT_NAME} ZXing)
    target_include_directories(${PROJECT_NAME} PRIVATE ZXing)


    option (LINK_CPP_STATICALLY "MSVC only, link standard library statically (/MT and /MTd)" OFF)

    add_definitions (-DUNICODE -D_UNICODE -D_CRT_SECURE_NO_WARNINGS)
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /MP")
    set (CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} /Oi /GS-")
    set (CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /Oi /GS-")
    if (LINK_CPP_STATICALLY)
        set(CMAKE_MFC_FLAG 1)
        
        set (CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} /MT")
        set (CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
        set (CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} /MTd")
        set (CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")
    else()
        add_definitions(-D_AFXDLL)
        set(CMAKE_MFC_FLAG 2)
    endif()




    set_property(TARGET ${PROJECT_NAME} PROPERTY VS_DEBUGGER_WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/$<CONFIG>")
target_compile_options(${PROJECT_NAME} PRIVATE "$<$<CONFIG:DEBUG>:${FLAGS}>" "$<$<CONFIG:RELEASE>:${FLAGS}>")

ELSEIF (UNIX)
ENDIF()

set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 17)

file(GLOB_RECURSE Screenshot 
${PROJECT_SOURCE_DIR}/Screenshot/*.cpp 
${PROJECT_SOURCE_DIR}/Screenshot/*.h)
file(GLOB_RECURSE Resource 
${PROJECT_SOURCE_DIR}/Screenshot/res/*
${PROJECT_SOURCE_DIR}/Screenshot.rc)

target_sources(${PROJECT_NAME} PUBLIC ${Screenshot} ${Resource})
source_group("Screenshot"            FILES ${Screenshot})
source_group("Resource"            FILES ${Resource})

message("PROJECT_SOURCE_DIR" ${PROJECT_SOURCE_DIR})
message("DEBUG_POSTFIX" ${DEBUG_POSTFIX})
message("CMAKE_CURRENT_BINARY_DIR" ${CMAKE_CURRENT_BINARY_DIR})
message("CMAKE_BINARY_DIR" ${CMAKE_BINARY_DIR})
message("CMAKE_INSTALL_INCLUDEDIR" ${CMAKE_INSTALL_INCLUDEDIR})
message("CMAKE_INSTALL_PREFIX: "  ${CMAKE_INSTALL_PREFIX})
message("CMAKE_INSTALL_BINDIR: "  ${CMAKE_INSTALL_BINDIR})
message("CMAKE_INSTALL_LIBDIR: "  ${CMAKE_INSTALL_LIBDIR})
message("CMAKE_INSTALL_DATADIR: "  ${CMAKE_INSTALL_DATADIR})
