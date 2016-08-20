project(telepathy-acid)

cmake_minimum_required(VERSION 2.8)

if (USE_QT4)
    find_package(TelepathyQt4 0.9.7 REQUIRED)
    find_package(TelepathyQt4Service 0.9.7 REQUIRED)

    find_package(TelegramQt4 REQUIRED)

    find_package(Qt4 4.6.0 REQUIRED QtCore QtNetwork)
else()
    find_package(TelepathyQt5 0.9.7 REQUIRED)
    find_package(TelepathyQt5Service 0.9.7 REQUIRED)

    find_package(TelegramQt5 REQUIRED)

    find_package(Qt5 REQUIRED COMPONENTS Core DBus Xml Network)
endif()

include(GNUInstallDirs)

add_subdirectory(src)

install(
    FILES data/acid.manager
    DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/telepathy/managers
)

install(FILES
    ${CMAKE_CURRENT_BINARY_DIR}/data/org.freedesktop.Telepathy.ConnectionManager.acid.service
    DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/dbus-1/services
)

install(
    FILES im-tox.svg
    DESTINATION share/icons/hicolor/scalable/apps
)
