set (LUABRIDGE_HEADERS
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/LuaBridge.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/RefCountedObject.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/RefCountedPtr.h
)
source_group ("LuaBridge" FILES ${LUABRIDGE_HEADERS})

set (LUABRIDGE_DETAIL_HEADERS
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/CFunctions.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/ClassInfo.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/Constructor.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/dump.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/FuncTraits.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/Iterator.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/LuaException.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/LuaHelpers.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/LuaRef.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/Namespace.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/Stack.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/TypeList.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/TypeTraits.h
	${CMAKE_CURRENT_SOURCE_DIR}/LuaBridge/detail/Userdata.h
)
source_group ("LuaBridge\\detail" FILES ${LUABRIDGE_DETAIL_HEADERS})

add_library (LuaBridge INTERFACE)
target_sources (LuaBridge INTERFACE
    ${LUABRIDGE_HEADERS}
    ${LUABRIDGE_DETAIL_HEADERS}
)
target_include_directories (LuaBridge INTERFACE .)

if (MSVC)
    add_custom_target (LuaBridgeFiles SOURCES
		${LUABRIDGE_HEADERS}
		${LUABRIDGE_DETAIL_HEADERS}
	)
endif ()
