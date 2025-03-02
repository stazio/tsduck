project('tsduck', 'cpp', default_options : ['cpp_std=c++20'])

#SCRIPTS_DIR = files('scripts')

# todo: removed 'linux' from list.
# moved 'freebsd', 'netbsd', 'openbsd', 'dragonflybsd', to be just 'bsd'
OTHER_OS = ['mac',  'bsd', 'windows']

CPP_ARGS = [
    '-DTS_NO_VATEK', '-DTS_NO_JAVA', '-DDTS_NO_PYTHON'
]

dtapi = dependency('dtapi', required: get_option('dektec'))
#vatek = dependency('vatek', required: get_option('vatek'))
srt = dependency('srt', required: get_option('srt'))
rist = dependency('librist', required: get_option('rist'))
pcsc = dependency('libpcsclite', required: get_option('pcsc'))
CORE_DEPS = [
    dtapi,
    srt,
    rist,
    pcsc
]

if not dtapi.found()
    CPP_ARGS += '-DTS_NO_DTAPI'
    CPP_ARGS += '-DTS_NO_DEKTEC'
endif

if not srt.found()
    CPP_ARGS += '-DTS_NO_SRT'
endif

if not rist.found()
    CPP_ARGS += '-DTS_NO_RIST'
endif

#if not vatek.found()
#    CPP_ARGS += '-DTS_NO_VATEK'
#endif

if not pcsc.found()
    CPP_ARGS += '-DTS_NO_PCSC'
endif

subdir('src/libtscore')
subdir('src/libtsduck')
subdir('src/tsplugins')
subdir('src/tstools')