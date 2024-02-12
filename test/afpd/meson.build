test_sources = [afpd_files, 'test.c', 'subtests.c', 'afpfunc_helpers.c']

test_deps = [kerberos, libgcrypt, mysqlclient]

test_libs = []

if not get_option('with-spotlight').disabled()
    test_sources += [
        meson.project_source_root() / 'etc/afpd/spotlight.c',
        meson.project_source_root() / 'etc/afpd/spotlight_marshalling.c',
    ]
    test_libs += libspotlight
    test_deps += [
        glib,
        talloc,
        tracker_sparql,
    ]
endif

if host_os != 'darwin'
    if not get_option('with-acls').disabled()
        test_sources += [
            meson.project_source_root() / 'etc/afpd/acls.c',
        ]
        test_deps += [acl_deps]
    endif
endif

afpdtest = executable(
    'afpdtest',
    test_sources,
    include_directories: root_includes,
    dependencies: test_deps,
    c_args: ['-DAPPLCNAME', dversion, messagedir, uamdir, confdir, statedir],
    link_with: [libatalk, test_libs],
)

test_sh = find_program('test.sh')

test('test1', test_sh)
test('test2', afpdtest)
