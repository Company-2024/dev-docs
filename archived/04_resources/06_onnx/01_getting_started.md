# Getting Started with ONNX

## Installation

There are three build variants for C#/C/C++ currently offered:

- **CPU:**
- **Microsoft.ML.OnnxRuntime.Gpu:**
- **Microsoft.ML.OnnxRuntime.DirectML:** View DirectML is a high-performance,
  hardware-accelerated DirectX 12 library for machine learning on Windows.

### Download

For Peralex AI projects, we will use the
[releases from Git](https://github.com/microsoft/onnxruntime/releases) rather
than dotnet or NuGet.

Go to the releases page and download the correct release version for you system
architecture e.g. onnxruntime-win-x64-1.16.2.zip for the CPU version on Windows
for an x64 system.

Extract the zip file and copy the parent directory of include, lib etc.
directories to
`\\iserver\development\libraries\com\github\microsoft\onnxruntime-x.xx.xx`

### Add to Visual Studio Project

See page on [Adding Package to Visual Studio](#). See the
[Troubleshooting section](#) for a known problem.

Some useful links are:

- [Building from source for inferencing](https://onnxruntime.ai/docs/build/inferencing)

## Examples

https://github.com/microsoft/onnxruntime-inference-examples/tree/main/c_cxx

### Troubleshooting

https://github.com/microsoft/onnxruntime/issues/6243
