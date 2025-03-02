sources = run_command('sh', '-c', 'echo *.cpp **/*.cpp **/**/*.cpp **/**/**/*.cpp', check: true).stdout().strip().split(' ')

# Filter out anything in a directory that matches OTHER_OS.
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

INC_DIRS = run_command('sh', '-c', 'echo */ **/*/ **/**/*/ **/**/**/*/', check: true).stdout().strip().split(' ')

TSDUCK_H = custom_target('tsduck.h', output: 'tsduck.h',  command: [meson.project_source_root() / 'scripts' / 'build-tsduck-header.py', 'tsduck', '@OUTPUT@'])

DEPS = [
    dependency('libcurl'),
    dependency('openssl'),
    dependency('readline'),
    dependency('tscore')
]

tsduck = library('tsduck', [SOURCES, TSDUCK_H], dependencies: DEPS, include_directories: INC_DIRS, install: true, cpp_args: CPP_ARGS)

# todo: Should tscore be an optional dependency?
tsduck_dep = declare_dependency(link_with: [tsduck], sources: [TSDUCK_H], include_directories: [INC_DIRS, '.'], dependencies: [dependency('tscore')])
meson.override_dependency('tsduck', tsduck_dep)