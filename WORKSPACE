
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

BAZEL_TOOLCHAIN_TAG = "0.6.3"

BAZEL_TOOLCHAIN_SHA = "da607faed78c4cb5a5637ef74a36fdd2286f85ca5192222c4664efec2d529bb8"

http_archive(
    name = "com_grail_bazel_toolchain",
    canonical_id = BAZEL_TOOLCHAIN_TAG,
    sha256 = BAZEL_TOOLCHAIN_SHA,
    strip_prefix = "bazel-toolchain-{tag}".format(tag = BAZEL_TOOLCHAIN_TAG),
    url = "https://github.com/grailbio/bazel-toolchain/archive/{tag}.tar.gz".format(tag = BAZEL_TOOLCHAIN_TAG),
)

http_archive(
    name = "com_google_absl",
    sha256 = "c696ed0f7fe14d2d5a95d89116dbeb0fa945d7c249c4c6ffc10a469c303628cb",
    strip_prefix = "abseil-cpp-73316fc3c565e5998983b0fb502d938ccddcded2",
    urls = ["https://github.com/abseil/abseil-cpp/archive/73316fc3c565e5998983b0fb502d938ccddcded2.zip"],  # master as of 2022-02-11
)

http_archive(
    name = "com_google_googletest",
    sha256 = "5cf189eb6847b4f8fc603a3ffff3b0771c08eec7dd4bd961bfd45477dd13eb73",
    strip_prefix = "googletest-609281088cfefc76f9d0ce82e1ff6c30cc3591e5",
    urls = ["https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip"],
)

http_archive(
    name = "rules_cc",
    sha256 = "4dccbfd22c0def164c8f47458bd50e0c7148f3d92002cdb459c2a96a68498241",
    urls = ["https://github.com/bazelbuild/rules_cc/releases/download/0.0.1/rules_cc-0.0.1.tar.gz"],
)

http_archive(
    name = "rules_foreign_cc",
    sha256 = "62e364a05370059f07313ec46ae4205af23deb00e41f786f3233a98098c7e636",
    strip_prefix = "rules_foreign_cc-ae4ff42901354e2da8285dac4be8329eea2ea96a",
    url = "https://github.com/bazelbuild/rules_foreign_cc/archive/ae4ff42901354e2da8285dac4be8329eea2ea96a.tar.gz",  # v 0.7.1
    patch_args = ["-p1"],
    patches = ["//:rules_foreign_cc.0.7.1.patch"],  # from https://github.com/bazelbuild/rules_foreign_cc/issues/859#issuecomment-1058361769
)



load("@rules_foreign_cc//foreign_cc:repositories.bzl", "rules_foreign_cc_dependencies")
load("@com_grail_bazel_toolchain//toolchain:deps.bzl", "bazel_toolchain_dependencies")
load("@com_grail_bazel_toolchain//toolchain:rules.bzl", "llvm_toolchain")

bazel_toolchain_dependencies()
llvm_toolchain(
    name = "llvm_toolchain",
    llvm_version = "13.0.0",
)

rules_foreign_cc_dependencies(
    register_built_tools = True,
)


load("@llvm_toolchain//:toolchains.bzl", "llvm_register_toolchains")

llvm_register_toolchains()


http_archive(
    name = "seal",
    sha256 = "616653498ba8f3e0cd23abef1d451c6e161a63bd88922f43de4b3595348b5c7e",
    strip_prefix = "SEAL-4.0.0",
    url = "https://github.com/microsoft/SEAL/archive/refs/tags/v4.0.0.tar.gz",
    patch_args = ["-p1"],
    patches = ["//:seal.4.0.0.patch"],
    build_file = "//:seal.BUILD",
)