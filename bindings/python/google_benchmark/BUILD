load("//bindings/python:build_defs.bzl", "py_extension")

exports_files(glob(["*.BUILD"]))
exports_files(["build_defs.bzl"])

py_library(
    name = "google_benchmark",
    srcs = ["__init__.py"],
    visibility = ["//visibility:public"],
    deps = [
        ":_benchmark",
    ],
)

py_extension(
    name = "_benchmark",
    srcs = ["benchmark.cc"],
    copts = [
        "-fexceptions",
        "-fno-strict-aliasing",
        "--std=c++17", # needed to use nanobind
    ],
    features = [
        "-use_header_modules",
        "-parse_headers",
    ],
    deps = [
        "//:benchmark",
        "@nanobind//:nanobind",
    ],
)

py_test(
    name = "example",
    srcs = ["example.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    visibility = ["//visibility:public"],
    deps = [
        ":google_benchmark",
    ],
)
