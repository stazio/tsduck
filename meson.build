project('tsduck', 'cpp', default_options : ['cpp_std=c++20'])

#SCRIPTS_DIR = files('scripts')

# todo: removed 'linux' from list.
# moved 'freebsd', 'netbsd', 'openbsd', 'dragonflybsd', to be just 'bsd'
OTHER_OS = ['mac',  'bsd', 'windows']

CPP_ARGS = [
    '-DTS_NO_DTAPI', '-DTS_NO_DEKTEC', '-DTS_NO_VATEK', '-DTS_NO_PCSC', '-DTS_NO_SRT', '-DTS_NO_RIST', '-DTS_NO_JAVA', '-DDTS_NO_PYTHON'
]

subdir('src/libtscore')
subdir('src/libtsduck')
subdir('src/tsplugins')
subdir('src/tstools')