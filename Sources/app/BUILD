load("@build_bazel_rules_apple//apple:macos.bzl", "macos_application")
load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")
load(
    "@rules_xcodeproj//xcodeproj:defs.bzl",
    "top_level_target",
    "xcodeproj",
)


swift_library(
    name = "app_lib",
    srcs = glob(["*.swift"]),
    visibility = ["//visibility:public"],
)


macos_application(
    name = "app",
    additional_contents = {
        "//Sources/bundle:com.example.app.bundle": "Library/SystemExtensions",
    },
    bundle_id = "com.example.app",
    bundle_name = "app",
    infoplists = ["Info.plist"],
    minimum_os_version = "11.0",
    version = "//:app_version",
    visibility = ["//visibility:public"],
    deps = [":app_lib"],
)

xcodeproj(
    name = "xcodeproj",
    project_name = "app",
    install_directory="",
    top_level_targets = [
        top_level_target(
            "//Sources/app:app",
            target_environments = ["device"]
        ),
        top_level_target(
            "//Sources/bundle:com.example.app.bundle",
            target_environments = ["device"]
        )
    ]
)