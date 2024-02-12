libatalk_sources = []
libatalk_libs = []

subdir('acl')
subdir('adouble')
subdir('bstring')
subdir('compat')
subdir('cnid')
subdir('dsi')
subdir('iniparser')
if talloc.found()
    subdir('talloc')
    libatalk_libs += libtalloc
endif
subdir('util')
subdir('unicode')
subdir('vfs')

libatalk = both_libraries(
    'atalk',
    libatalk_sources,
    include_directories: root_includes,
    dependencies: [acl_deps, mysqlclient, threads],
    link_with: [libdsi],
    link_whole: [
        libacl,
        libadouble,
        libatalk_libs,
        libbstring,
        libcnid,
        libcompat,
        libdsi,
        libiniparser,
        libunicode,
        libutil,
        libvfs,
    ],
    soversion: 18,
    install: true,
)
