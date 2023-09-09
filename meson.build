project('little-hell-example', 'c', default_options: ['buildtype=debugoptimized', 'c_std=c99'])
add_project_arguments('-Wfatal-errors', '-Wpedantic', language: 'c')

package_name = 'Little Hell Example'
package_string = 'little-hell-example'
package_tarname = 'littlehellexample'
package_version = '1.0'

config_header = configure_file(input: './config.h.in',
               output: 'config.h',
               configuration: {
                  'PACKAGE_NAME': package_name,
                  'PACKAGE_STRING': package_string,
                  'PACKAGE_TARNAME': package_tarname,
                  'PACKAGE_VERSION': package_version,
})

config_dep = declare_dependency(
   include_directories: include_directories('.'),
   sources: config_header
)


# Look the 'littlehell' dependency.
engine_dep = dependency('littlehell', required: false)

# If the dependency isn't installed system-wide, build the subproject:
if not engine_dep.found()
    littlehell_subproj = subproject('engine')
    littlehell_dep = littlehell_subproj.get_variable('littlehell_dep')
endif

subdir('src/game')
#subdir('src/server')

