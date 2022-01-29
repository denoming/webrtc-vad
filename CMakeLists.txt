
set(VAD ${COMPONENT_DIR}/webrtc/common_audio/vad)
set(SPL ${COMPONENT_DIR}/webrtc/common_audio/signal_processing)
set(RTC ${COMPONENT_DIR}/webrtc/rtc_base)

idf_component_register(
    SRCS ${VAD}/vad_core.c
         ${VAD}/vad_filterbank.c
         ${VAD}/vad_gmm.c
         ${VAD}/vad_sp.c
         ${VAD}/webrtc_vad.c
         ${SPL}/energy.c
         ${SPL}/resample_48khz.c
         ${SPL}/resample_fractional.c
         ${SPL}/resample_by_2_internal.c
         ${SPL}/spl_init.c
         ${SPL}/min_max_operations.c
         ${SPL}/downsample_fast.c
         ${SPL}/get_scaling_square.c
         ${SPL}/vector_scaling_operations.c
         ${SPL}/division_operations.c
         ${SPL}/cross_correlation.c
         ${RTC}/checks.cc
    INCLUDE_DIRS ${VAD}/include
    PRIV_INCLUDE_DIRS ${COMPONENT_DIR}/webrtc
)

target_compile_definitions(${COMPONENT_TARGET}
    PRIVATE "-DWEBRTC_POSIX"
)
