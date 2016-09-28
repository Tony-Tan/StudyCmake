cmake_minimum_required(VERSION 3.6)

###################################################################
#CMD2
###################################################################
option(USE_MYMATH "Use tutorial provided math implementation" ON)

if(USE_MYMATH)
	include_directories("${PROJECT_SOURCE_DIR}/MathFunctions")
	add_subdirectory(MathFunctions)
	set(EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif(USE_MYMATH)
###################################################################
#CMD1
###################################################################
#版本号
set (TUTORIAL_VERSION_MAJOR 1)
set (TUTORIAL_VERSION_MINOR 0)
#配置头文件，想源代码传递信息
configure_file(
	${PROJECT_SOURCE_DIR}/TutorialConfig.h.in
	${PROJECT_BINARY_DIR}/TutorialConfig.h
)
#将二进制文件树添加到包含文件的搜索路径，可以找到TutorialConfig.h
include_directories(${PROJECT_BINARY_DIR})

###################################################################

###################################################################
add_executable(Tutorial tutorial.cxx)
target_link_libraries(Tutorial ${EXTRA_LIBS})
