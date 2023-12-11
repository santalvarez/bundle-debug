load("@build_bazel_rules_apple//apple:macos.bzl", "macos_bundle")
load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")



swift_library(
    name = "bundle_lib",
    srcs = glob(["*.swift"]),
    visibility = ["//visibility:public"],
)


macos_bundle(
    name = "com.example.app.bundle",
    bundle_extension = "systemextension",
    bundle_id = "com.example.app.bundle",
    linkopts = ["-execute"],
    infoplists = ["Info.plist"],
    minimum_os_version = "11.0",
    version = "//:app_version",
    visibility = ["//visibility:public"],
    deps = [":bundle_lib"],
)
