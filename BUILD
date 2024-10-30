load("@rules_cc//cc:defs.bzl", "cc_test")

cc_test(
    name = "cpp_bazel_gtest",
    srcs = ["example_test.cpp"],
    deps = [
        "//src:your_library",  # Replace with the actual path to your library
        "@gtest//:gtest_main",
    ],
)

cc_test(
    name = "sample_tests",
    srcs = ["example_test.cpp"],
    deps = [
        "//src:your_library",  # Replace with the actual path to your library
        "@gtest//:gtest_main",
    ],
)