Minimal reproduction of rules_rust #2980

## Steps

1. Install bazel
1. Build with `bazel build //:bazel_test`

## Error

The error is:

```
ERROR: /home/slee/.cache/bazel/_bazel_slee/0709329b1bdae20569dc2d8208532527/external/rules_rust++crate+crates__kube-core-0.98.0/BUILD.bazel:16:13: Compiling Rust rlib kube_core v0.98.0 (25 files) failed: (E
xit 1): process_wrapper failed: error executing Rustc command (from target @@rules_rust++crate+crates__kube-core-0.98.0//:kube_core) bazel-out/k8-opt-exec-ST-d57f47055a04/bin/external/rules_rust+/util/proce
ss_wrapper/process_wrapper --arg-file ... (remaining 81 arguments skipped)

Use --sandbox_debug to see verbose messages from the sandbox and retain the sandbox build root for debugging
error[E0433]: failed to resolve: could not find `apimachinery` in `k8s_openapi`
  --> external/rules_rust++crate+crates__kube-core-0.98.0/src/dynamic.rs:10:18
   |
10 | use k8s_openapi::apimachinery::pkg::apis::meta::v1::ObjectMeta;
   |                  ^^^^^^^^^^^^ could not find `apimachinery` in `k8s_openapi`

```

... and so on, complaining about every memeber of the `apimachinery` module.
