filegroup(
    name = "sources",
    srcs = glob(["*.c"]),
    visibility = ["//applications/sumobot:__subpackages__"],
)

filegroup(
    name = "headers",
    srcs = glob(["*.h"]),
    visibility = ["//applications/sumobot:__subpackages__"],
)

cc_library(
    name = "sysHwCfg_init",
    srcs = [":sources"],
    hdrs = [":headers"],
    deps = [],
    includes = ["."],
    visibility = ["//applications/sumobot:__subpackages__"],
)
