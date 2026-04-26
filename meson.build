project('StartWine',
	version: '421',
	license: 'GPL-3.0'
)

# Paths to source (.po) and target (.mo) localization files
pt_mo = meson.current_source_dir() / 'data' / 'scripts' / 'locale' / 'pt' / 'LC_MESSAGES' / 'StartWine.mo'
ru_mo = meson.current_source_dir() / 'data' / 'scripts' / 'locale' / 'ru' / 'LC_MESSAGES' / 'StartWine.mo'
zh_mo = meson.current_source_dir() / 'data' / 'scripts' / 'locale' / 'zh' / 'LC_MESSAGES' / 'StartWine.mo'

pt_po = meson.current_source_dir() / 'data' / 'scripts' / 'locale' / 'pt' / 'LC_MESSAGES' / 'pt.po'
ru_po = meson.current_source_dir() / 'data' / 'scripts' / 'locale' / 'ru' / 'LC_MESSAGES' / 'ru.po'
zh_po = meson.current_source_dir() / 'data' / 'scripts' / 'locale' / 'zh' / 'LC_MESSAGES' / 'zh.po'

# Commands for compiling translations
convert_pt_po = [find_program('msgfmt'), pt_po, '-o', pt_mo]
convert_ru_po = [find_program('msgfmt'), ru_po, '-o', ru_mo]
convert_zh_po = [find_program('msgfmt'), zh_po, '-o', zh_mo]

# Performing compilation localization files
run_command(convert_pt_po)
run_command(convert_ru_po)
run_command(convert_zh_po)

# Install icon
install_data('data/img/gui_icons/sw_icon.svg',
	install_dir: join_paths(get_option('datadir'), 'icons', 'hicolor', 'scalable', 'apps'),
	rename: 'startwine.svg'
)

# Prepare and install start file
configure_file(input: 'data/startwine.in',
	output: 'startwine',
	install_dir: join_paths(get_option('bindir')),
	install: true,
	install_mode: 'rwxr-xr-x',
	configuration: {
		'VERSION': meson.project_version(),
	}
)

# Install desktop file
configure_file(input: 'data/ru.launcher.StartWine.desktop.in',
	output: 'ru.launcher.StartWine.desktop',
	install_dir: join_paths(get_option('datadir'), 'applications'),
	install: true,
	install_mode: 'rw-r--r--',
	configuration: {}
)

# Install program data
install_subdir('data',
	install_dir: join_paths(get_option('datadir'), 'startwine'),
	exclude_files: ['startwine.in', 'ru.launcher.StartWine.desktop.in']
)
