# netcore_2_2_webapi
.NET Core 2.2 profiling demo


## Build and run on Linux amd64

```shell
cd netcore_2_2_webapi 
dotnet publish -c Release

DDTRACE_HOME="$(pwd)/bin/Release/netcoreapp2.2/publish/datadog";
DD_DOTNET_TRACER_HOME="$DDTRACE_HOME" \
CORECLR_ENABLE_PROFILING=1 \
CORECLR_PROFILER="{846F5F1C-F9AE-4B07-969E-05C26BC060D8}" \
CORECLR_PROFILER_PATH="$DDTRACE_HOME/linux-x64/Datadog.Trace.ClrProfiler.Native.so" \
LD_PRELOAD="$DDTRACE_HOME/linux-x64/Datadog.Linux.ApiWrapper.x64.so" \
DD_PROFILING_ENABLED=1 \
DD_PROFILING_WALLTIME_ENABLED=1 \
DD_PROFILING_CPU_ENABLED=1 \
DD_PROFILING_EXCEPTION_ENABLED=1 \
DD_PROFILING_ALLOCATION_ENABLED=1 \
DD_PROFILING_LOCK_ENABLED=1 \
DD_PROFILING_HEAP_ENABLED=1 \
DD_PROFILING_GC_ENABLED=1 \
DD_SERVICE=dotnet-profiling-demo DD_ENV=testing DD_VERSION=1.2.3 \
DD_AGENT_HOST=127.0.0.1 DD_TRACE_AGENT_PORT=9529 \
dotnet bin/Release/netcoreapp2.2/publish/netcore_2_2.dll


```