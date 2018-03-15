`[brian@elephant ~]$ klist`
```
klist: No credentials cache found (filename: /tmp/krb5cc_1000)
```
`[brian@elephant ~]$ kinit`
```
Password for brian@CDH.BOOTCAMP.BB:
```
`[brian@elephant ~]$ klist`
```
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: brian@CDH.BOOTCAMP.BB

Valid starting       Expires              Service principal
2018-03-15 11:01:18  2018-03-16 11:01:18  krbtgt/CDH.BOOTCAMP.BB@CDH.BOOTCAMP.BB
	renew until 2018-03-22 11:01:18
```

######Get to sentry-install.md
