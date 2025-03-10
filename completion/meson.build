generate_completions_program = find_program('generate_completions.py')

if bash_completion.found()
  bash_comp_dir = bash_completion.get_pkgconfig_variable('completionsdir')
else
  bash_comp_dir = get_option('datadir') / 'bash-completion' / 'completions'
  message('bash-completion not found: using', get_option('prefix') / bash_comp_dir, 'as a falback install directory')
endif

if fish.found()
  fish_comp_dir = fish.get_pkgconfig_variable('completionsdir')
else
  fish_comp_dir = get_option('datadir') / 'fish' / 'completions'
  message('fish not found: using', get_option('prefix') / fish_comp_dir, 'as a fallback install directory')
endif

completion_bash = custom_target('bash-completion',
  capture: true,
  command: [generate_completions_program, meson.global_source_root() / 'src', 'bash'],
  install: true,
  install_dir: bash_comp_dir,
  output: 'toolbox')

completion_zsh = custom_target('zsh-completion',
  capture: true,
  command: [generate_completions_program, meson.global_source_root() / 'src', 'zsh'],
  install: true,
  install_dir: get_option('datadir') / 'zsh' / 'site_functions',
  output: '_toolbox')

completion_fish = custom_target('fish-completion',
  capture: true,
  command: [generate_completions_program, meson.global_source_root() / 'src', 'fish'],
  install: true,
  install_dir: fish_comp_dir,
  output: 'toolbox.fish')
