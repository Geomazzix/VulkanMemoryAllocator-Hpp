cmake_minimum_required(VERSION 3.29)

project(
    vma
    VERSION 3.1.0
    DESCRIPTION "C++ bindings for the VulkanMemoryAllocator library."
    LANGUAGES C CXX
)

find_package(Vulkan REQUIRED)

add_library(vma INTERFACE)

target_include_directories(vma SYSTEM
    INTERFACE
        ${Vulkan_INCLUDE_DIRS}
        ${Vulkan_INCLUDE_DIRS}/vma #never change the source files, hence this is added.
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
)

target_link_libraries(vma
    INTERFACE
        Vulkan::Vulkan
)