SOURCES_MAC = [
]

SOURCES_BSD = [
]

SOURCES_WIN = [
    'network/windows/tsWebRequestGuts.cpp',
    'system/windows/tsComIds.cpp'
]

# todo: Consider these sources depending on OS.
SOURCES_BAD = [SOURCES_MAC, SOURCES_BSD, SOURCES_WIN]

sources = run_command('sh', '-c', 'echo *.cpp **/*.cpp **/**/*.cpp', check: true).stdout().strip().split(' ')

# Filter out any parameters not in windows.
SOURCES = []
foreach source : sources
    valid = true
    foreach part : source.split('/')
        if part in OTHER_OS
            valid = false
            break
        endif
    endforeach

    if valid
        SOURCES += source
    endif
endforeach

INC_DIRS = run_command('sh', '-c', 'echo */ **/*/', check: true).stdout().strip().split(' ')

DEPS = [
    dependency('libcurl'),
    dependency('openssl'),
    dependency('readline'),
    dependency('zlib'),
    CORE_DEPS
]

TSCORE_H = custom_target('tscore.h', output: 'tscore.h',  command: [meson.project_source_root() / 'scripts' / 'build-tsduck-header.py', 'tscore', '@OUTPUT@'])

tscore = library('tscore', [SOURCES, TSCORE_H], dependencies: DEPS, include_directories: INC_DIRS, install: true, cpp_args: CPP_ARGS)

tscore_dep = declare_dependency(link_with: [tscore], include_directories: [INC_DIRS, '.'])
meson.override_dependency('tscore', tscore_dep)