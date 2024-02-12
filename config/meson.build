afp_conf = fs.exists(pkgconfdir / 'afp.conf')

if afp_conf
else
    install_data('afp.conf.tmpl', rename: 'afp.conf', install_dir: pkgconfdir)
endif

install_data('extmap.conf', install_dir: pkgconfdir)

install_data('netatalk-dbus.conf', install_dir: prefix / 'etc/dbus-1/system.d')

install_data('README', install_dir: localstatedir / 'netatalk')

install_data('README', install_dir: localstatedir / 'netatalk/CNID')

if have_pam
    subdir('pam')
endif
