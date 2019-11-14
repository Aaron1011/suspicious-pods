# Suspicious pods

![crates.io](https://img.shields.io/crates/v/suspicious-pods.svg)

Suspicious pods is a very simple tool, which does a very simple task: print a list of pods in your Kubernetes cluster that might not be working correctly, along with a reason on why that pod is considered suspicious.

Example:

```
$ suspicious-pods -- help
suspicious-pods 0.4
Prints a list of k8s pods that might not be working correctly

USAGE:
    suspicious-pods.exe <namespace> --format <format>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -f, --format <format>    The output format. Valid values are: text, markdown [default: text]

ARGS:
    <namespace>    The namespace you want to scan [default: default]
    
$ suspicious-pods

fluentd-aggregator-0/fluentd-aggregator                         Restarted 6 times. Last exit code: 1. (Error)
fluentd-dgjm8/fluentd                                           Waiting: PodInitializing
jaeger-es-index-cleaner-120860-jd7b4/jaeger-es-index-cleaner    Waiting: ImagePullBackOff
jaeger-operator-5545d554cb-mf5zt/jaeger-operator                Restarted 3 times. Last exit code: 137. (OOMKilled)
thanos-store-gateway-0                                          Stuck on init container: wait-for-prometheus
```

This is useful in big deployments, when you have a large number of pods and you just want to get a quick glimpse of what might be failing in your cluster.

## Installation

### Option 1: Precompiled binaries

Head to the releases and download your binary. There are binaries for Windows and Linux. On Windows, you need to have OpenSSL installed on your machine through [vcpkg](https://github.com/Microsoft/vcpkg)

### Option 2: Cargo

Install [rustup](https://rustup.rs/) and run `cargo install suspicious-pods`. If you are on Windows, you need to have OpenSSL installed on your machine through [vcpkg](https://github.com/Microsoft/vcpkg) and set the environment variable `VCPKGRS_DYNAMIC=1`.


## Feedback

Feedback and contributions are welcome! Please open an issue or a PR.
