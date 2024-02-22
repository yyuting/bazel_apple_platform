# Issue with Bazel Platform + Apple Rules

Building a hello world `ios_build_test` target. The target is set to only be compatible with ios arm64 device (not simulator).

Build succeeds with a custom platform and explicit platform mapping:

`bazel test //:ios_build_tests --platforms=//:platform_ios`

But building with the default platform from apple_support would fail, it seems apple rules is picking up `ios_sim_arm64` instead for the `cc_library` that the `ios_build_test` target depends on.

`bazel test //:ios_build_tests --platforms=@build_bazel_apple_support//platforms:ios_arm64`

```
Target //:ios_build_tests failed to build
Use --verbose_failures to see the command lines of failed build steps.
ERROR: Analysis of target '//:ios_build_tests' failed; build aborted: Target //:ios_build_tests is incompatible and cannot be built, but was explicitly requested.
Dependency chain:
    //:ios_build_tests (7e114e)
    //:hello_world (9a2e98)   <-- target platform (@@build_bazel_apple_support//platforms:ios_sim_arm64) didn't satisfy constraint @@platforms//:incompatible
INFO: Elapsed time: 0.097s, Critical Path: 0.00s
INFO: 1 process: 1 internal.
ERROR: Build did NOT complete successfully
ERROR: No test targets were found, yet testing was requested
```
