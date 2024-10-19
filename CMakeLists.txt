cmake_minimum_required(VERSION 3.10)

project(helloworld VERSION 0.0.1)  # Укажите версию проекта

# Установите стандарт C++
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Найдите библиотеку Boost, если она нужна (если не нужна, удалите эту часть)
find_package(Boost COMPONENTS unit_test_framework REQUIRED)

# Создайте исполняемый файл из main.cpp
add_executable(helloworld main.cpp)

# Если вы используете Boost, добавьте ссылки на него
target_link_libraries(helloworld PRIVATE ${Boost_LIBRARIES})

# Опции компиляции (для предупреждений)
if (MSVC)
    target_compile_options(helloworld PRIVATE /W4)
else ()
    target_compile_options(helloworld PRIVATE -Wall -Wextra -pedantic -Werror)
endif()

# Установки для CPack (если вы планируете использовать CPack для сборки пакетов)
include(CPack)

# Установки для тестирования (если вы планируете добавлять тесты в будущем)
enable_testing()