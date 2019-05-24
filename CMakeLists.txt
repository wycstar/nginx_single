cmake_minimum_required(VERSION 3.12)
project(nginx_single C)

set(CMAKE_C_STANDARD 99)

file(GLOB CORE_SOURCE core/*.c)
file(GLOB CORE_HEADER core/*.h)

file(GLOB EVENT_SOURCE event/*.c)
file(GLOB EVENT_HEADER event/*.h)

file(GLOB HTTP_SOURCE http/*.c)
file(GLOB HTTP_HEADER http/*.h)

file(GLOB MAIL_SOURCE mail/*.c)
file(GLOB MAIL_HEADER mail/*.h)

file(GLOB MISC_SOURCE misc/*.c)
file(GLOB MISC_HEADER misc/*.h)

file(GLOB OS_SOURCE os/*.c)
file(GLOB OS_HEADER os/*.h)

file(GLOB STREAM_SOURCE stream/*.c)
file(GLOB STREAM_HEADER stream/*.h)

aux_source_directory(. SRC_LIST)
aux_source_directory(./core SRC_LIST)
aux_source_directory(./event SRC_LIST)
aux_source_directory(./event/modules SRC_LIST)
aux_source_directory(./os/unix SRC_LIST)
aux_source_directory(./http SRC_LIST)
aux_source_directory(./http/modules SRC_LIST)

add_executable(${PROJECT_NAME} ${SRC_LIST})

INCLUDE_DIRECTORIES(./)
INCLUDE_DIRECTORIES(./core)
INCLUDE_DIRECTORIES(./event)
INCLUDE_DIRECTORIES(./event/modules)
INCLUDE_DIRECTORIES(./os/unix)
INCLUDE_DIRECTORIES(./http)
INCLUDE_DIRECTORIES(./http/modules)
INCLUDE_DIRECTORIES(./mail)

INCLUDE_DIRECTORIES(/opt/local/include)

#add_executable(nginx_single main.c
#        ngx_auto_config.h
#        ngx_auto_headers.h
#        ngx_modules.c
#        core/nginx.h core/nginx.c
#        core/ngx_array.c core/ngx_array.h
#
#        core/ngx_config.h core/ngx_core.h)
#        ${CORE_SOURCE} ${CORE_HEADER}
#        ${EVENT_SOURCE} ${EVENT_HEADER}
#        ${HTTP_SOURCE} ${HTTP_HEADER}
#        ${MAIL_SOURCE} ${MAIL_HEADER}
#        ${MISC_SOURCE} ${MISC_HEADER}
#        ${OS_SOURCE} ${OS_HEADER}
#        ${STREAM_SOURCE} ${STREAM_HEADER})
