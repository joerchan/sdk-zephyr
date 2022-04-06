# SPDX-License-Identifier: Apache-2.0

zephyr_sources(
  soc.c
  )

zephyr_library_sources_ifdef(CONFIG_PM
  power.c
  )

zephyr_library_sources_ifdef(CONFIG_NRF53_SYNC_RTC
  sync_rtc.c
  )
zephyr_library_include_directories(
  ${NRF_DIR}/include/tfm
)

if (CONFIG_BUILD_WITH_TFM)
  zephyr_library_include_directories(
    ${NRF_DIR}/include/tfm
    $<TARGET_PROPERTY:tfm,TFM_BINARY_DIR>/install/interface/include
  )
endif()
