project('dtapi', 'cpp', version: 'v2025.01.0')
dtapi = static_library('dtapi', objects: 'LinuxSDK/DTAPI/Lib/GCC7.5.0/DTAPI64.o')
dtapi_dep = declare_dependency(link_with: dtapi, include_directories: 'LinuxSDK/DTAPI/Include')
meson.override_dependency('dtapi', dtapi_dep)