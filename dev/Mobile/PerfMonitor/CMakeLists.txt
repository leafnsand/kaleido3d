find_package(Qt5 COMPONENTS Core Widgets Gui OpenGL)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)
	
file(GLOB PM_VIEWS_SRC "Views/*.h" "Views/*.cpp" "Views/Base/*.h" "Views/Base/*.cpp")
source_group(Views FILES ${PM_VIEWS_SRC})
file(GLOB PM_SRVS_SRC "Services/*.h" "Services/*.cpp")
source_group(Services FILES ${PM_SRVS_SRC})
add_definitions(-D_WIN32_WINNT=0x600 -D_SCL_SECURE_NO_WARNINGS -D_CRT_SECURE_NO_WARNINGS -D_WINSOCK_DEPRECATED_NO_WARNINGS)
set(MAIN_SRC MainFrame.h MainFrame.cpp Main.cpp)
source_group(MainFrame FILES ${MAIN_SRC})
include_directories(.)
add_executable(PerfMon ${PM_VIEWS_SRC} ${PM_SRVS_SRC} ${MAIN_SRC} Resources.qrc)
target_link_libraries(PerfMon Qt5::Core Qt5::Widgets Qt5::Gui Qt5::OpenGL Kaleido3D.Core DeviceBridge)
set_target_properties(PerfMon PROPERTIES FOLDER "Tools/Mobile")