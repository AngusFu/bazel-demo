workspace(
    name = "react_webpack",
    managed_directories = {"@npm": ["node_modules"]},
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "2eca5b934dee47b5ff304f502ae187c40ec4e33e12bcbce872a2eeb786e23269",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/1.4.1/rules_nodejs-1.4.1.tar.gz"],
)

# https://bazelbuild.github.io/rules_nodejs/Built-ins.html
load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories", "yarn_install")

node_repositories(
    node_urls = ["http://npm.taobao.org/mirrors/node/v{version}/{filename}"],
    node_version = "12.13.0",
    package_json = ["//:package.json"],
    yarn_version = "1.19.1",
)

yarn_install(
    # Name this npm so that Bazel Label references look like @npm//package
    name = "npm",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)

load("@npm//:install_bazel_dependencies.bzl", "install_bazel_dependencies")

install_bazel_dependencies()

# https://bazelbuild.github.io/rules_nodejs/TypeScript.html
load("@npm_bazel_typescript//:index.bzl", "ts_setup_workspace")

ts_setup_workspace()
