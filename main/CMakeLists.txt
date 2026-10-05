# Embed CA, certificate & key directly into binary
set(COMPONENT_ADD_INCLUDEDIRS
    "."
    "${CMAKE_CURRENT_LIST_DIR}"
)

idf_component_register(
    SRCS
        "ds18b20.c"
        "wpa2_enterprise_main.c"
        "aws.c"

    INCLUDE_DIRS
        ${COMPONENT_ADD_INCLUDEDIRS}

    EMBED_TXTFILES
        wpa2_ca.pem
        wpa2_client.crt
        wpa2_client.key

    REQUIRES
        coreMQTT

    PRIV_REQUIRES
        esp_wifi
        esp_event
        nvs_flash
        esp_timer
        esp_driver_gpio
        wpa_supplicant
        ssd1306
        backoffAlgorithm
        posix_compat
)
