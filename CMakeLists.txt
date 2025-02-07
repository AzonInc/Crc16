
# The following lines of boilerplate have to be in your project's
# CMakeLists in this exact order for cmake to work correctly
cmake_minimum_required(VERSION 3.5)

# Arduino install using IDF component manager
if(__COMPONENT_TARGETS MATCHES "___idf_espressif__arduino-esp32")
    list(APPEND ESP_NIMBLE_PRIV_REQUIRES
        arduino-esp32
    )
# Manual installation of Arduino framework
elseif(__COMPONENT_TARGETS MATCHES "__idf_arduino")
    list(APPEND ESP_NIMBLE_PRIV_REQUIRES
        arduino
    )
# PlatformIO
elseif(__COMPONENT_TARGETS MATCHES "___idf_framework-arduinoespressif32")
    list(APPEND ESP_NIMBLE_PRIV_REQUIRES
        framework-arduinoespressif32
    )
endif()

idf_component_register(
  INCLUDE_DIRS
    "src"
  SRCS
    "src/Crc16.cpp"
  PRIV_REQUIRES
    ${ESP_NIMBLE_PRIV_REQUIRES}
)