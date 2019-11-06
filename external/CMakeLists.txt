include(ExternalProject)
find_package(Git REQUIRED)
# find_package(Hg REQUIRED)
include(DSVExtensions)

#------------------------------------------------------------------------------
# Convenience update all, dependencies are added in ExternalHeaderOnly_Add
add_custom_target(update COMMENT "Updated all external projects")

#------------------------------------------------------------------------------
# Catch - Unit test header only library

# For details about ExternalHeaderOnly_Add see cmake/DSVExtensions.cmake

# target_link_libraries (DSV PRIVATE catch)
# #include <catch.hpp>
ExternalHeaderOnly_Add(Catch
		"https://github.com/catchorg/Catch2.git" "master" "single_include/catch2")


#------------------------------------------------------------------------------
# GLM - Crossplatform graphics math library
ExternalHeaderOnly_Add(glm
		 "https://github.com/g-truc/glm.git" "master" "glm/glm.hpp")

add_subdirectory(${glm_SOURCE_DIR} EXCLUDE_FROM_ALL)
find_package(glm REQUIRED)

#------------------------------------------------------------------------------
# GLFW - Clorssplatform graphics context library


ExternalDownloadNowGit(glfw https://github.com/glfw/glfw.git master)
add_subdirectory(${glfw_SOURCE_DIR} EXCLUDE_FROM_ALL)
find_package(glfw3 REQUIRED)

#------------------------------------------------------------------------------
# Corrade - crossplatform utility library


#ExternalDownloadNowGit(corrade https://github.com/mosra/corrade.git master)
#option(BUILD_corrade_TESTS "" OFF) #disable tests
#option(USE_SYSTEM_corrade "" ON ) #use system curl
#add_subdirectory(${corrade_SOURCE_DIR} EXCLUDE_FROM_ALL)
# Make headers come as SYSTEM, to get rid of all warning on included headers
#set_directory_properties(PROPERTIES CORRADE_USE_PEDANTIC_FLAGS ON)
#set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${corrade_SOURCE_DIR}/modules)
#find_package(Corrade REQUIRED Main)


#------------------------------------------------------------------------------
# Magnum - C++ Graphics framwork

#ExternalDownloadNowGit(magnum https://github.com/mosra/magnum.git master)
# Add Magnum as a subproject, enable Sdl2Application
#set(WITH_SDL2APPLICATION ON CACHE BOOL "" FORCE)
#set(WITH_ANYIMAGEIMPORTER ON CACHE BOOL "" FORCE)
#set(WITH_TGAIMPORTER ON CACHE BOOL "" FORCE)
#set(WITH_OBJIMPORTER ON CACHE BOOL "" FORCE)
#set(WITH_ANYSCENEIMPORTER ON CACHE BOOL "" FORCE)
#set(WITH_MAGNUMFONT ON CACHE BOOL "" FORCE)
#add_subdirectory(${magnum_SOURCE_DIR} EXCLUDE_FROM_ALL)
#set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${magnum_SOURCE_DIR}/modules)
#find_package(Magnum REQUIRED
#	GL
#	MeshTools
#	Primitives
#	Shaders
# SceneGraph
#	Trade
#	Text
#	Sdl2Application
#)

#------------------------------------------------------------------------------
# MagnumPlugins

#ExternalDownloadNowGit(magnum_plugins https://github.com/mosra/magnum-plugins.git master)
# Add MagnumPlugins as a subproject, enable TrueType font and importers
#set(WITH_STBTRUETYPEFONT ON CACHE BOOL "" FORCE)
#set(WITH_DDSIMPORTER ON CACHE BOOL "" FORCE)
#set(WITH_STBIMAGEIMPORTER ON CACHE BOOL "" FORCE)
#set(WITH_TINYGLTFIMPORTER ON CACHE BOOL "" FORCE)
#add_subdirectory(${magnum_plugins_SOURCE_DIR} EXCLUDE_FROM_ALL)
#set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${magnum_plugins_SOURCE_DIR}/modules)
#find_package(MagnumPlugins REQUIRED
#	StbImageImporter
#	TinyGltfImporter
#	DdsImporter
#	StbTrueTypeFont
#)
#add_custom_target(plugins ALL DEPENDS
#	Magnum::AnyImageImporter
#	Magnum::AnySceneImporter
#	Magnum::ObjImporter
#	Magnum::TgaImporter
#	Magnum::MagnumFont
#	MagnumPlugins::StbImageImporter
#	MagnumPlugins::TinyGltfImporter
#	MagnumPlugins::DdsImporter
#	MagnumPlugins::StbTrueTypeFont
#)

#------------------------------------------------------------------------------
# MagnumExtras

#ExternalDownloadNowGit(magnum_extras https://github.com/mosra/magnum-extras.git master)
# Add MagnumExtras as a subproject, enable Ui
#set(WITH_UI ON CACHE BOOL "" FORCE)
#add_subdirectory(${magnum_extras_SOURCE_DIR} EXCLUDE_FROM_ALL)
#set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${magnum_extras_SOURCE_DIR}/modules)
#find_package(MagnumExtras REQUIRED
#	Ui
#)
#add_custom_target (extras ALL DEPENDS
#	MagnumExtras::Ui
#)
#------------------------------------------------------------------------------
# Examples of other external projects
#------------------------------------------------------------------------------

#------------------------------------------------------------------------------
# target_link_libraries (DSV PRIVATE json)
# #include <nlohmann/json.hpp>
# ExternalHeaderOnly_Add(json
#     "https://github.com/nlohmann/json.git" "master" "single_include")

#------------------------------------------------------------------------------
# target_link_libraries (DSV PRIVATE spdlog)
# #include <spdlog/spdlog.h>
# Bundled fmt can be used: #include <spdlog/fmt/fmt.h>
# spdlog::error("Some error message with arg: {}", 1);
# ExternalHeaderOnly_Add(spdlog
#     "https://github.com/gabime/spdlog.git" "v1.x" "include")

#------------------------------------------------------------------------------
# target_link_libraries (DSV PRIVATE doctest)
# #include <doctest.h>
# ExternalHeaderOnly_Add("DocTest"
#     "https://github.com/onqtam/doctest.git" "master" "src/DocTest")

#------------------------------------------------------------------------------
# target_link_libraries (DSV PRIVATE fmt)
# #include <fmt/format.h>
# Use with: `fmt::print("Hello {} - {}!\n", "world", 3.56f);`

# ExternalDownloadNowGit(fmt "https://github.com/fmtlib/fmt.git" "master")
# add_library(fmt STATIC ${fmt_SOURCE_DIR}/src/format.cc)
# target_include_directories(fmt SYSTEM PUBLIC ${fmt_SOURCE_DIR}/include)
# # target_compile_definitions(spdlog INTERFACE -DSPDLOG_FMT_EXTERNAL) #if using SPDLOG


#------------------------------------------------------------------------------
# cpr - HTTP(S) requests library with nice interface

# target_link_libraries (DSV PRIVATE fmt)
# #include <cpr/cpr.h>
# auto r = cpr::Get(cpr::Url{"https://ohnheiser.cz"});
# cout<<r.text<<endl;

# find_package(CURL REQUIRED)
# ExternalDownloadNowGit(cpr https://github.com/finkandreas/cpr.git master)
# option(BUILD_CPR_TESTS "" OFF) #disable tests
# option(USE_SYSTEM_CURL "" ON ) #use system curl
# add_subdirectory(${cpr_SOURCE_DIR} EXCLUDE_FROM_ALL)
# # Make headers come as SYSTEM, to get rid of all warning on included headers
# target_include_directories(cpr SYSTEM PUBLIC ${CPR_INCLUDE_DIRS} ${CURL_INCLUDE_DIRS})


