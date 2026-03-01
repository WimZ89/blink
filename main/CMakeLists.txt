idf_component_register(SRCS "blink_example_main.c"
                       INCLUDE_DIRS "."
                       PRIV_REQUIRES esp_wifi nvs_flash esp_event esp_netif led_strip esp_driver_gpio freertos log esp_hw_support)
