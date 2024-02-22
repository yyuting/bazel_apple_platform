load("@build_bazel_rules_apple//apple:ios.bzl", "ios_build_test")

platform(
    name = "platform_ios",
    constraint_values = [
        "@platforms//os:ios",
        "@platforms//cpu:arm64",
        "@build_bazel_apple_support//constraints:device",
    ],
)

config_setting(
    name = "ios_arm64",
    values = {
        "cpu": "ios_arm64",
        "ios_multi_cpus": "arm64",
        "apple_platform_type": "ios",
    },
)

cc_library(
    name = "hello_world",
    srcs = ["hello_world.cpp"],
    target_compatible_with = select({
        ":ios_arm64": [],
        "//conditions:default": ["@platforms//:incompatible"],
    }),
)

ios_build_test(
    name = "ios_build_tests",
    minimum_os_version = "17.0",
    tags = ["ios"],
    targets = [":hello_world"],
)