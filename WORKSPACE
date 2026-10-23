load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# Bazel 8 needs toolchain helpers absent from protobuf's rules_cc dependency.
http_archive(
    name = "rules_cc",
    sha256 = "712d77868b3152dd618c4d64faaddefcc5965f90f5de6e6dd1d5ddcd0be82d42",
    strip_prefix = "rules_cc-0.1.1",
    urls = [
        "https://github.com/bazelbuild/rules_cc/releases/download/0.1.1/rules_cc-0.1.1.tar.gz",
    ],
)

# Bazel 8 initializes Java dependencies through rules_java_deps.bzl.
http_archive(
    name = "rules_java",
    sha256 = "bbe7d94360cc9ed4607ec5fd94995fd1ec41e84257020b6f09e64055281ecb12",
    urls = [
        "https://github.com/bazelbuild/rules_java/releases/download/8.14.0/rules_java-8.14.0.tar.gz",
    ],
)

# Bazel 8 removed the native Python providers used by older rules_python.
http_archive(
    name = "rules_python",
    sha256 = "690e0141724abb568267e003c7b6d9a54925df40c275a870a4d934161dc9dd53",
    strip_prefix = "rules_python-0.40.0",
    urls = [
        "https://github.com/bazelbuild/rules_python/releases/download/0.40.0/rules_python-0.40.0.tar.gz",
    ],
)

# Keep protobuf rules and their path helpers available to Go dependencies.
http_archive(
    name = "rules_proto",
    sha256 = "0e5c64a2599a6e26c6a03d6162242d231ecc0de219534c38cb4402171def21e8",
    strip_prefix = "rules_proto-7.0.2",
    urls = [
        "https://github.com/bazelbuild/rules_proto/releases/download/7.0.2/rules_proto-7.0.2.tar.gz",
    ],
)

http_archive(
    name = "bazel_skylib",
    sha256 = "bc283cdfcd526a52c3201279cda4bc298652efa898b10b4db0837dc51652756f",
    urls = [
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.7.1/bazel-skylib-1.7.1.tar.gz",
    ],
)

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "6dc2da7ab4cf5d7bfc7c949776b1b7c733f05e56edc4bcd9022bb249d2e2a996",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_go/releases/download/v0.39.1/rules_go-v0.39.1.zip",
        "https://github.com/bazelbuild/rules_go/releases/download/v0.39.1/rules_go-v0.39.1.zip",
    ],
)

http_archive(
    name = "bazel_gazelle",
    sha256 = "727f3e4edd96ea20c29e8c2ca9e8d2af724d8c7778e7923a854b2c80952bc405",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-gazelle/releases/download/v0.30.0/bazel-gazelle-v0.30.0.tar.gz",
        "https://github.com/bazelbuild/bazel-gazelle/releases/download/v0.30.0/bazel-gazelle-v0.30.0.tar.gz",
    ],
)

http_archive(
    name = "com_google_protobuf",
    sha256 = "2e442d21839ec9dbafda4cc9083239aa04e78fc9c27dfa59b5374e968050cd22",
    strip_prefix = "protobuf-29.0",
    urls = [
        "https://github.com/protocolbuffers/protobuf/releases/download/v29.0/protobuf-29.0.zip",
    ],
)

load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")
load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies")
load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")
load("//:deps.bzl", "go_dependencies")

go_register_toolchains(version = "1.20.4")

go_rules_dependencies()

gazelle_dependencies()

# gazelle:repository_macro deps.bzl%go_dependencies
go_dependencies()

protobuf_deps()
