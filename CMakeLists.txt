cmake_minimum_required (VERSION 3.15)

add_library(luabind STATIC
	src/class.cpp
	src/class_info.cpp
	src/class_registry.cpp
	src/class_rep.cpp
	src/create_class.cpp
	src/error.cpp
	src/find_best_match.cpp
	src/function.cpp
	src/implicit_cast.cpp
	src/link_compatibility.cpp
	src/object_rep.cpp
	src/open.cpp
	src/overload_rep.cpp
	src/pcall.cpp
	src/ref.cpp
	src/scope.cpp
	src/stack_content_by_name.cpp
	src/weak_ref.cpp
	src/wrapper_base.cpp
)

# cmake_policy(SET CMP0092 "NEW")
# string(REGEX REPLACE "/W[3|4]" "/w" CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")

target_compile_options(luabind
    PRIVATE "-w"
)

target_include_directories(luabind PUBLIC include ../lua/include C:/local/boost_1_74_0)

target_link_libraries(luabind PUBLIC lua_static)
target_compile_features(luabind PUBLIC cxx_std_20)
add_definitions(-DLUA_COMPAT_5_3 -DBOOST_BIND_GLOBAL_PLACEHOLDERS)
