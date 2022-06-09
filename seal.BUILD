load("@rules_foreign_cc//foreign_cc:defs.bzl", "cmake")

package(
    default_visibility = ["//visibility:public"],
)

filegroup(
    name = "all_srcs",
    srcs = glob(["**"]),
    visibility = ["//:__pkg__"],
)

cmake(
    name = "seal",
    build_args = [
        "--verbose",
    ],
    cache_entries = {
        "CMAKE_C_FLAGS": "-fPIC",
        "CMAKE_BUILD_TYPE": "Release",
        "BUILD_SHARED_LIBS": "OFF",
        # "SEAL_THROW_ON_TRANSPARENT_CIPHERTEXT": "OFF",
        "SEAL_BUILD_DEPS": "ON",
        "SEAL_USE_MSGSL": "ON",
        "SEAL_USE_ZLIB": "ON",
        "SEAL_USE_ZSTD": "ON",
    },
    lib_source = ":all_srcs",
    out_static_libs = [
        "libseal-4.0.a",
    ],
    tags = ["requires-network"],
)