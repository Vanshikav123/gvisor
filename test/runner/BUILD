load("//tools:defs.bzl", "bzl_library", "go_binary")

package(
    default_applicable_licenses = ["//:license"],
    licenses = ["notice"],
)

go_binary(
    name = "runner",
    testonly = 1,
    srcs = ["main.go"],
    data = [
        "//runsc",
        "//test/runner/fuse",
        "//test/runner/setup_container",
    ],
    visibility = ["//:sandbox"],
    deps = [
        "//pkg/cleanup",
        "//pkg/log",
        "//pkg/sentry/seccheck",
        "//pkg/state/pretty",
        "//pkg/state/statefile",
        "//pkg/test/testutil",
        "//runsc/specutils",
        "//test/runner/gtest",
        "//test/trace/config",
        "//test/uds",
        "@com_github_moby_sys_capability//:go_default_library",
        "@com_github_opencontainers_runtime_spec//specs-go:go_default_library",
        "@org_golang_x_sys//unix:go_default_library",
    ],
)

bzl_library(
    name = "defs_bzl",
    srcs = ["defs.bzl"],
    visibility = ["//visibility:private"],
    deps = ["//tools:defs_bzl"],
)
