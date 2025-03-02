PLUGINS = run_command('sh', '-c', 'echo *.cpp', check: true).stdout().strip().split(' ')
TSPLUGINS = []

foreach plugin : PLUGINS
    lib = library(plugin.split('.cpp')[0], plugin, dependencies: tsduck_dep, install: true, name_prefix: '')
    TSPLUGINS += [declare_dependency(link_with:lib)]
endforeach