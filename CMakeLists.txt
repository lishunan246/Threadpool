cmake_minimum_required(VERSION 2.6)
project(Threadpool)
if(WIN32)
    message(STATUS ">>> Windows")
else()
    message(STATUS ">>> Not Windows")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
endif()

add_library(threadpool STATIC 
    Threadpool.cpp
    ThreadpoolTimer.cpp
    ThreadpoolWork.cpp
    ThreadpoolWait.cpp
    ThreadpoolIo.cpp
    Threadpool.h
    ThreadpoolTimer.h
    ThreadpoolWork.h
    ThreadpoolWait.h
    ThreadpoolIo.h
    ThreadpoolWaitObject.h
    ThreadpoolWaitObject.cpp
)

add_executable(
    TPTest main.cpp
)

target_link_libraries(TPTest threadpool)

add_executable(
	TPWorkTest TPWorkTest.cpp
)

target_link_libraries(TPWorkTest threadpool)

add_executable(
	TPWaitTest TPWaitTest.cpp
)

target_link_libraries(TPWaitTest threadpool)

add_executable(
	TPTimerTest TPTimerTest.cpp
)

target_link_libraries(TPTimerTest threadpool)