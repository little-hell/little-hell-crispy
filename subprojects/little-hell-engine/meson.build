project('little-hell-engine', 'c', default_options: ['default_library=static', 'buildtype=debugoptimized', 'c_std=c99'])

# We need LOG_USE_COLOR for the rxi/log.c library
add_project_arguments('-DLOG_USE_COLOR', language: 'c')

cc = meson.get_compiler('c')

math = cc.find_library('m', required: true)

if host_machine.system() == 'windows'
    # Windows-specific configurations
    static_sdl_linkage = true
elif host_machine.system() == 'linux'
    # Linux-specific configurations
    static_sdl_linkage = false
else
    # Configurations for other operating systems
    static_sdl_linkage = false
endif

sdl2 = dependency('SDL2', static: static_sdl_linkage)
sdl2_net = dependency('SDL2_net', static: static_sdl_linkage)
sdl2_mixer = dependency('SDL2_mixer', static: static_sdl_linkage)

src_dir = 'src'
system_src_dir = 'system'

# Source files only used by the game binary
engine_source_files = files(
    src_dir / 'aes_prng.c',
    src_dir / 'a11y.c',
    src_dir / 'crispy.c',

    src_dir / 'd_event.c',
    src_dir / 'doomtype.h',
    src_dir / 'd_mode.c',
    src_dir / 'd_iwad.c',
    src_dir / 'd_loop.c',
    src_dir / 'i_input.c',

    src_dir / 'gusconf.c',


    # Eventually, we will have:
    #src_dir / system_src_dir / 'system.c',
    #src_dir / system_src_dir / 'exit.c',
    #src_dir / system_src_dir / 'sleep.c',

    # But for now:
    src_dir / 'i_system.c',

    src_dir / 'i_joystick.c',
    src_dir / 'i_cdmus.c',
    src_dir / 'i_endoom.c',
    src_dir / 'i_videohr.c',
    src_dir / 'i_musicpack.c',
    src_dir / 'i_oplmusic.c',
    src_dir / 'i_pcsound.c',
    src_dir / 'i_sdlsound.c',
    src_dir / 'i_sdlmusic.c',
    src_dir / 'i_flmusic.c',
    src_dir / 'i_sound.c',
    src_dir / 'i_timer.c',
    src_dir / 'i_video.c',
    src_dir / 'midifile.c',
    src_dir / 'mus2mid.c',
    src_dir / 'm_argv.c',
    src_dir / 'm_bbox.c',
    src_dir / 'm_cheat.c',
    src_dir / 'm_config.c',
    src_dir / 'm_controls.c',
    src_dir / 'm_misc.c',
    src_dir / 'm_fixed.c',
    src_dir / 'net_client.c',
    src_dir / 'net_common.c',
    src_dir / 'net_dedicated.c',
    src_dir / 'net_gui.c',
    src_dir / 'net_defs.h',
    src_dir / 'net_io.c',
    src_dir / 'net_loop.c',
    src_dir / 'net_packet.c',
    src_dir / 'net_petname.c',
    src_dir / 'net_query.c',
    src_dir / 'net_sdl.c',
    src_dir / 'net_server.c',
    src_dir / 'net_structrw.c',
    src_dir / 'sha1.c',
    src_dir / 'memio.c',
    src_dir / 'tables.c',
    src_dir / 'v_diskicon.c',
    src_dir / 'v_video.c',
    src_dir / 'v_trans.c',
    src_dir / 'w_checksum.c',
    src_dir / 'w_main.c',
    src_dir / 'w_merge.c',
    src_dir / 'w_wad.c',
    src_dir / 'w_file.c',
    src_dir / 'w_file_stdc.c',
    src_dir / 'w_file_posix.c',
    src_dir / 'w_file_win32.c',
    src_dir / 'z_native.c'
  )


# Compile 3rd-party libraries inside the repository

libs_src_dir = 'libs'

# Source files for the OPL emulation library
opl_source_dir =  libs_src_dir / 'opl'
opl_source_files = files(
    opl_source_dir / 'opl3.c',
    opl_source_dir / 'opl.c',
    opl_source_dir / 'opl_queue.c',
    opl_source_dir / 'opl_sdl.c',
    opl_source_dir / 'opl_timer.c',
)

opl = library('opl', opl_source_files, dependencies: sdl2_mixer)

# rxi/log.c logging library
log_source_dir = libs_src_dir / 'log'
log_source_files = files (
    log_source_dir / 'log.c'
)

log = library('log', log_source_files)

# Source files for the textscreen library
textscreen_source_dir =  libs_src_dir / 'textscreen'
textscreen_source_files = files(
    textscreen_source_dir / 'txt_button.c',
    textscreen_source_dir / 'txt_checkbox.c',
    textscreen_source_dir / 'txt_conditional.c',
    textscreen_source_dir / 'txt_desktop.c',
    textscreen_source_dir / 'txt_dropdown.c',
    textscreen_source_dir / 'txt_fileselect.c',
    textscreen_source_dir / 'txt_gui.c',
    textscreen_source_dir / 'txt_inputbox.c',
    textscreen_source_dir / 'txt_io.c',
    textscreen_source_dir / 'txt_label.c',
    textscreen_source_dir / 'txt_radiobutton.c',
    textscreen_source_dir / 'txt_scrollpane.c',
    textscreen_source_dir / 'txt_sdl.c',
    textscreen_source_dir / 'txt_separator.c',
    textscreen_source_dir / 'txt_spinctrl.c',
    textscreen_source_dir / 'txt_strut.c',
    textscreen_source_dir / 'txt_table.c',
    textscreen_source_dir / 'txt_utf8.c',
    textscreen_source_dir / 'txt_widget.c',
    textscreen_source_dir / 'txt_window_action.c',
    textscreen_source_dir / 'txt_window.c',
    textscreen_source_dir / 'txt_button.c',
    textscreen_source_dir / 'txt_checkbox.c',
    textscreen_source_dir / 'txt_conditional.c',
    textscreen_source_dir / 'txt_desktop.c',
    textscreen_source_dir / 'txt_dropdown.c',
    textscreen_source_dir / 'txt_fileselect.c',
    textscreen_source_dir / 'txt_gui.c',
    textscreen_source_dir / 'txt_inputbox.c',
    textscreen_source_dir / 'txt_io.c',
    textscreen_source_dir / 'txt_label.c',
    textscreen_source_dir / 'txt_radiobutton.c',
    textscreen_source_dir / 'txt_scrollpane.c',
    textscreen_source_dir / 'txt_sdl.c',
    textscreen_source_dir / 'txt_separator.c',
    textscreen_source_dir / 'txt_spinctrl.c',
    textscreen_source_dir / 'txt_strut.c',
    textscreen_source_dir / 'txt_table.c',
    textscreen_source_dir / 'txt_utf8.c',
    textscreen_source_dir / 'txt_widget.c',
    textscreen_source_dir / 'txt_window_action.c',
    textscreen_source_dir / 'txt_window_action.h',
    textscreen_source_dir / 'txt_window.c',
)

textscreen = library('textscreen', textscreen_source_files, dependencies: sdl2_mixer)

# Source files for the PC sound
pcsound_source_dir =  libs_src_dir / 'pcsound'
pcsound_source_files = files(
    pcsound_source_dir / 'pcsound_bsd.c',
    pcsound_source_dir / 'pcsound.c',
    pcsound_source_dir / 'pcsound.h',
    pcsound_source_dir / 'pcsound_internal.h',
    pcsound_source_dir / 'pcsound_linux.c',
    pcsound_source_dir / 'pcsound_sdl.c',
    pcsound_source_dir / 'pcsound_win32.c',
)

pcsound = library('pcsound', pcsound_source_files, dependencies: sdl2_mixer)

#littlehell_include_dir = 'include/'

littlehell_lib = library('littlehell', engine_source_files,
    include_directories: [
      include_directories(libs_src_dir),
      #include_directories(littlehell_include_dir),
      include_directories(src_dir)
    ],
    dependencies: [
      sdl2,
      sdl2_net,
      sdl2_mixer,
      math
    ],
    link_with: [
      textscreen,
      pcsound,
      opl,
      log
    ]
)

# When declaring the dependency, also specify the include directories.

if meson.is_subproject()
    littlehell_dep = declare_dependency(
      link_with: littlehell_lib,
      dependencies: [
        sdl2,
        sdl2_net,
        sdl2_mixer,
        math,
      ],
      include_directories: [
        include_directories(libs_src_dir),
        include_directories(src_dir),
        #include_directories(littlehell_include_dir)
      ]
    )
endif

run_target('clang-tidy',
    command : 'scripts/clang-tidy.sh')

run_target('clang-format',
    command : 'scripts/clang-format.sh')

run_target('cppcheck',
    command : 'scripts/cppcheck.sh')

