project(
  'wayfire-plugin-fydecor',
  'c',
  'cpp',
  version: '0.1',
  license: 'MIT',
  meson_version: '>=0.51.0',
  default_options: [
    'cpp_std=gnu++2b',
    'c_std=c11',
    'warning_level=2',
    'werror=false',
  ],
)

wayfire = dependency('wayfire')
wlroots = dependency('wlroots')
wfconfig = dependency('wf-config')
cairo = dependency('cairo')
pango = dependency('pango')
pangocairo = dependency('pangocairo')
pixman = dependency('pixman-1')

add_project_arguments(['-DWLR_USE_UNSTABLE'], language: ['cpp','c'])
add_project_arguments(['-DWAYFIRE_PLUGIN'], language: ['cpp','c'])
add_project_link_arguments(['-rdynamic'], language: 'cpp')

decoration = shared_module(
  'fydecor',
  [
    'decoration.cpp',
    'deco-subsurface.cpp',
    'deco-button.cpp',
    'deco-layout.cpp',
    'deco-theme.cpp'
  ],
  #include_directories: [wayfire_api_inc, wayfire_conf_inc, plugins_common_inc],
  dependencies: [wlroots, pixman, wfconfig, cairo, pango, pangocairo],
  install: true,
  install_dir: join_paths(get_option('libdir'),'wayfire')
)
install_data( 'fydecor.xml', install_dir: wayfire.get_variable( pkgconfig: 'metadatadir') )


