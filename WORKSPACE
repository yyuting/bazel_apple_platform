workspace(name = "bazel_apple_platform")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# Bazel Skylib.
http_archive(
    name = "bazel_skylib",
    urls = ["https://github.com/bazelbuild/bazel-skylib/releases/download/1.4.1/bazel-skylib-1.4.1.tar.gz"],
    sha256 = "b8a1527901774180afc798aeb28c4634bdccf19c4d98e7bdd1ce79d1fe9aaad7",
)

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

bazel_skylib_workspace()

load("@bazel_skylib//lib:versions.bzl", "versions")

versions.check(
    maximum_bazel_version = "7.0.2",
    minimum_bazel_version = "7.0.2",
)

# Bazel rules_apple.
http_archive(
    name = "build_bazel_rules_apple",
    urls = ["https://github.com/bazelbuild/rules_apple/releases/download/3.2.1/rules_apple.3.2.1.tar.gz"],
    sha256 = "9c4f1e1ec4fdfeac5bddb07fa0e872c398e3d8eb0ac596af9c463f9123ace292",
)

load(
    "@build_bazel_rules_apple//apple:repositories.bzl",
    "apple_rules_dependencies",
)

apple_rules_dependencies()

load(
    "@build_bazel_apple_support//lib:repositories.bzl",
    "apple_support_dependencies",
)

apple_support_dependencies()