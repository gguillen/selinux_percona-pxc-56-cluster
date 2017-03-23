# SELinux rules for Percona XtraDB Cluster 5.6
**Because turning SELinux off isn't always an option**

This module is known to work with rsync and xtrabackup-v2 SST methods.  Other SST methods may not function correctly with this policy module.

I've used a subset of this rule for several years with Percona XtraDB Cluster 5.5, but I have not tested this exact version on 5.5.  This module *should* work just fine for 5.5.

Installation
------------

Run the following with root privileges on all your nodes:

1. If you do not already have SELinux tools installed, run: `yum install policycoreutils-python`
2. Run `semanage port -m -t mysqld_port_t -p tcp 4444`
3. Run `semanage port -a -t mysqld_port_t -p tcp 4567`
4. Run `semanage port -a -t mysqld_port_t -p tcp 4568`
5. Run `semodule -i percona-pxc-56-cluster.pp` to import the policy module

Thanks
------

Thanks to Martin from my old thread in the Percona Google group (https://groups.google.com/forum/#!topic/percona-discussion/beyXK3U0ySo) who posted the last piece to make this work with xtrabackup.
