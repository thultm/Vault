> Model Analyzer is a CLI tool to help with a better understanding of the compute and memory requirements of the Triton Inference Server models by sweeping through configurations settings and generating reports summarizing performance.

With Model Analyzer users can:
- Run customizable configuration sweeps to identify the best possible configuration for the expected workload and hardware.
- Summarize findings about latency, throughput, GPU resource utilizations, power draw and more, with detailed reports, metrics and graphs. These reports help compare performance across different configurations of setup.
- Tailor model deployments to cater to user's Quality of Service requirements like specific p99 latency limits, GPU memory utilization and minimum throughput!
# Usage details
## Model Analyzer Modes
> `-m` or `--mode` tells the model analyzer the context in which it is being run.
### Online Mode
- This is the default mode. 
- When in this mode, Model Analyzer will operate to find the optimal model configuration for an online inference scenario.
- By default in online mode, the best model configuration will be the one that maximizes throughput.
### Offline Mode 
- The offline mode `--mode=offline` tells Model Analyzer to operate to find the optimal model configuration for an offline inference scenario. 
- By default in offline mode, the best model configuration will be the one that maximizes throughput.
## Subcommand 
### `profile`
- The `profile` subcommand begins by loading the "latest" checkpoint (if available) in the checkpoint directory.
- It will then run model inferences using perf analyzer, and collect metrics like throughput, latency and memory usage for any measurements not present in the checkpoint.