#Challenge Setup

####In the file challenges/labs/0_setup.md
######Cloud provider: Azure

######List your instances
```
[brian@lion ~]$ getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
10.3.2.5        elephant.cdh-bootcamp-bb elephant
10.3.2.4        lion.cdh-bootcamp-bb lion
10.3.2.6        horse.cdh-bootcamp-bb horse
10.3.2.9        monkey.cdh-bootcamp-bb monkey
```

######List the Linux release you are using
```
[brian@lion ~]$ uname -or
3.10.0-514.28.1.el7.x86_64 GNU/Linux
```
######List the file system capacity for the first node
```
[brian@lion ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        32G  4,8G   27G  16% /
devtmpfs         14G     0   14G   0% /dev
tmpfs            14G     0   14G   0% /dev/shm
tmpfs            14G  8,3M   14G   1% /run
tmpfs            14G     0   14G   0% /sys/fs/cgroup
/dev/sda1       497M  117M  381M  24% /boot
/dev/sdb1        55G  2,1G   51G   4% /mnt/resource
tmpfs           2,8G     0  2,8G   0% /run/user/1000
```

######List the command and output for yum repolist enabled
```
[brian@lion ~]$ yum repolist enabled

Loaded plugins: langpacks, product-id, search-disabled-repos
Repo rhui-rhel-7-server-dotnet-rhui-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-dotnet-rhui-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-dotnet-rhui-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-dotnet-rhui-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-dotnet-rhui-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-dotnet-rhui-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-extras-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-extras-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-extras-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-extras-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-extras-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-extras-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-optional-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-optional-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-optional-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-optional-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-optional-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-optional-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-rh-common-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-rh-common-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-rh-common-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-rh-common-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-rh-common-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-rh-common-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-supplementary-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-supplementary-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-supplementary-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-supplementary-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-7-server-rhui-supplementary-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-7-server-rhui-supplementary-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-server-rhui-rhscl-7-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-server-rhui-rhscl-7-debug-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-server-rhui-rhscl-7-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-server-rhui-rhscl-7-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
Repo rhui-rhel-server-rhui-rhscl-7-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content.crt
Repo rhui-rhel-server-rhui-rhscl-7-source-rpms forced skip_if_unavailable=True due to: /etc/pki/rhui/key.pem
epel/x86_64/metalink                                                             |  29 kB  00:00:00     
epel                                                                             | 4.7 kB  00:00:00     
rhui-microsoft-azure-rhel7                                                       | 2.9 kB  00:00:00     
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/dotnet/1/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/extras/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/optional/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rh-common/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/supplementary/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/debug/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/os/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-2.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-3.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
https://rhui-1.microsoft.com/pulp/repos//content/dist/rhel/rhui/server/7/7Server/x86_64/rhscl/1/source/SRPMS/repodata/repomd.xml: [Errno 14] curl#58 - "unable to load client cert: -8018 (SEC_ERROR_UNKNOWN_PKCS11_ERROR)"
Trying other mirror.
(1/3): epel/x86_64/group_gz                                                                                                                                                                 | 266 kB  00:00:00     
(2/3): epel/x86_64/primary_db                                                                                                                                                               | 6.3 MB  00:00:00     
(3/3): epel/x86_64/updateinfo                                                                                                                                                               | 903 kB  00:00:00     
repo id                                                                                   repo name                                                                                                          status
epel/x86_64                                                                               Extra Packages for Enterprise Linux 7 - x86_64                                                                     12.401                                                         17
rhui-microsoft-azure-rhel7                                                                Microsoft Azure RPMs for Red Hat Enterprise Linux 7                                                                     2
repolist: 12.420
```

####Add the following Linux accounts to all nodes

######User hilary with a UID of 2800 

```
sudo groupadd analytics
sudo groupadd datasci
sudo useradd -u 2800 -g datasci hilary
sudo useradd -u 2900 -g analytics anupam
```

######List the /etc/passwd entries for hilary and anupam
```
[brian@elephant ~]$ cat /etc/passwd | grep hilary
hilary:x:2800:1002::/home/hilary:/bin/bash

[brian@elephant ~]$ cat /etc/passwd | grep anupam
anupam:x:2900:1001::/home/anupam:/bin/bash

```

######List the /etc/group entries for analytics and datasci
```
[brian@elephant ~]$ cat /etc/group | grep analytics
analytics:x:1001:
[brian@elephant ~]$ cat /etc/group | grep datasci
datasci:x:1002:
```