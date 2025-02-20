load("@rules_java//java:defs.bzl", "java_library")

# Copyright 2018 The Bazel Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
package(default_visibility = ["//src:__subpackages__"])

_COMMON_DEPS = [
    "//src/main/kotlin/io/bazel/kotlin/builder",
    "//src/main/kotlin/io/bazel/kotlin/builder/toolchain",
    "//src/main/kotlin/io/bazel/kotlin/builder/utils:utils",
    "//src/main/protobuf:kotlin_model_java_proto",
    "//src/main/protobuf:deps_java_proto",
    "@kotlin_rules_maven//:com_google_truth_truth",
    "@kotlin_rules_maven//:junit_junit",
    "@kotlin_rules_maven//:com_google_guava_guava",
    "@kotlin_rules_maven//:com_google_code_findbugs_jsr305",
]

java_library(
    name = "test_lib",
    testonly = 1,
    srcs = [
        "Deps.java",
        "DirectoryType.java",
        "JdepsMergerTestComponent.java",
        "KotlinAbstractTestBuilder.java",
        "KotlinBuilderTestComponent.java",
        "KotlinJsTestBuilder.java",
        "KotlinJvmTestBuilder.java",
    ],
    data = [
        "//src/main/kotlin/io/bazel/kotlin/compiler",
        "@com_github_jetbrains_kotlin//:home",
    ],
    exports = _COMMON_DEPS + [
        "@kotlin_rules_maven//:com_google_protobuf_protobuf_java",
    ],
    runtime_deps = [
        "@bazel_tools//tools/jdk:JacocoCoverage",
        "@com_github_jetbrains_kotlin//:kotlin-reflect",
        "@com_github_jetbrains_kotlin//:kotlin-stdlib",
    ],
    deps = _COMMON_DEPS + [
        "//third_party:autovalue",
        "//third_party:dagger",
        "@kotlin_rules_maven//:javax_annotation_javax_annotation_api",
        "//src/main/kotlin/io/bazel/kotlin/builder/tasks",
    ],
)

test_suite(
    name = "builder_tests",
    tests = [
        "//src/test/kotlin/io/bazel/kotlin/builder/tasks",
        "//src/test/kotlin/io/bazel/kotlin/builder/utils",
    ],
    visibility = ["//visibility:public"],
)
