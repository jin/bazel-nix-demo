load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_tweag_rules_nixpkgs",
    urls = ["https://github.com/tweag/rules_nixpkgs/archive/v0.5.2.tar.gz"],
    strip_prefix = "rules_nixpkgs-0.5.2",
    sha256 = "5a384daa57b49abf9f0b672852f1a66a3c52aecf9d4d2ac64f6de0fd307690c8",
)

load("@io_tweag_rules_nixpkgs//nixpkgs:nixpkgs.bzl", "nixpkgs_git_repository", "nixpkgs_package", "nixpkgs_cc_configure")

nixpkgs_git_repository(
    name = "nixpkgs",
    revision = "7b8a7cee78468919b98cc4c8694d84165f28ef68", # Any tag or commit hash
    sha256 = "" # optional sha to verify package integrity!
)

PACKAGES = ["maven", "bazelisk"]

[nixpkgs_package(
    name = package,
    repositories = { "nixpkgs": "@nixpkgs//:default.nix" },
) for package in PACKAGES]

nixpkgs_cc_configure(
    nix_file = "//nixpkgs:cc-toolchain.nix",
    repository = "@nixpkgs",
)
