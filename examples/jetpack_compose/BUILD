load("@io_bazel_rules_kotlin//kotlin:core.bzl", "define_kt_toolchain", "kt_compiler_plugin")
load("@io_bazel_rules_kotlin//kotlin:jvm.bzl", "kt_jvm_import")
load("@bazel_tools//tools/jdk:default_java_toolchain.bzl", "default_java_toolchain")

# Java Toolchain

default_java_toolchain(
    name = "java_toolchain",
    visibility = ["//visibility:public"],
)

define_kt_toolchain(
    name = "kotlin_toolchain",
    api_version = "1.6",
    jvm_target = "1.8",
    language_version = "1.6",
)

# Define the compose compiler plugin
# Used by referencing //:jetpack_compose_compiler_plugin

kt_compiler_plugin(
    name = "jetpack_compose_compiler_plugin",
    id = "androidx.compose.compiler",
    target_embedded_compiler = True,
    visibility = ["//visibility:public"],
    deps = [
        "@maven//:androidx_compose_compiler_compiler",
    ],
)

# Add missing 'sun.misc' files to coroutines artifact
# Used in 'override_targets' by referencing @//:kotlinx_coroutines_core_jvm
kt_jvm_import(
    name = "kotlinx_coroutines_core_jvm",
    jars = ["@maven_secondary//:v1/https/repo1.maven.org/maven2/org/jetbrains/kotlinx/kotlinx-coroutines-core-jvm/1.6.3/kotlinx-coroutines-core-jvm-1.6.3.jar"],
    srcjar = "@maven_secondary//:v1/https/repo1.maven.org/maven2/org/jetbrains/kotlinx/kotlinx-coroutines-core-jvm/1.6.3/kotlinx-coroutines-core-jvm-1.6.3-sources.jar",
    visibility = ["//visibility:public"],
    deps = [
        "//stub:sun_misc",
        "@maven//:org_jetbrains_kotlin_kotlin_stdlib",
    ],
)
