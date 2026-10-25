cc_test(
    name = "sysHwCfg_init_test",
    size = "small",
    srcs = [
        "sysHwCfg_init_test.cc",
        "//applications/sumobot/components/sysHwCfg/code:sources",
        "//applications/sumobot/components/sysHwCfg/code:headers",
    ],
    deps = [
        "@googletest//:gtest",
        "@googletest//:gtest_main",
        "@emb_platform//avr8/mcal/test:mcal_avr_h",
    ],
    includes = [
        "../code",
    ],
)
