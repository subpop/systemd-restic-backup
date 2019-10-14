project('systemd-restic-backup')

systemd = dependency('systemd')
set_variable('unit_dir', join_paths(systemd.get_pkgconfig_variable('prefix'), 'lib', 'systemd', 'system'))
set_variable('user_unit_dir', join_paths(systemd.get_pkgconfig_variable('prefix'), 'lib', 'systemd', 'user'))

unit_files = files('restic-backup.service',
                   'restic-backup.timer',
                   'restic-prune.service',
                   'restic-prune.timer')
instantiated_unit_files = files('restic-backup@.service',
                                'restic-backup@.timer',
                                'restic-prune@.service',
                                'restic-prune@.timer')

install_data(unit_files,
             install_mode: 'rw-r--r--',
             install_dir: get_variable('user_unit_dir'))
install_data(instantiated_unit_files,
             install_mode: 'rw-r--r--',
             install_dir: get_variable('unit_dir'))