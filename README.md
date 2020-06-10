# nfsmounts
Mounts nfs volumes via LDAP on nfs clients
Shoot me question about it at dlinuxguy@gmail.com

                                                         ____________________
                                                        |  dc=yourorg,dc=com |
                                                         --------------------
                                                                |
                                                                |
                                                 ________________________________
                                                | ou=netMounts,dc=yourorg,dc=com |
                                                 --------------------------------
                                                /                                 \
                                               /                                   \
                                              /                                     \
                                             /                                       \
      ______________________________________________                                   ______________________________________________
     | ou=nfsClients,ou=netMounts,dc=yourorg,dc=com |                                 | ou=nfsVolumes,ou=netMounts,dc=yourorg,dc=com |
      ----------------------------------------------                                   ----------------------------------------------
        |                                                                                 |
        |                                                                                 |
        |  ____________________________________________________________________           |  _________________________________________
        |-| dn: hostname=appclt-1,ou=nfsClients,ou=netMounts,dc=yourorg,dc=com |          |-|volumepath=nfsserver:/vol/appdata/data1 |
        |  --------------------------------------------------------------------              -----------------------------------------
        |       |                                                                               |
        |       |  _____________________________________________________                        |  _____________________________________
        |       |-| mountpoint=/opt/data1                               |                       |-| hostname=appclt-1
        |         | volumepath=nfsserver1:/vol/appdata/data1            |                         |
        |         | mountoptions=rw,async,wrize=1024,rsize=1034         |
        |         | mountcomment=App data1                              |
        |         | mountdisabled=FALSE                                 |
        |          -----------------------------------------------------
        |  ____________________________________________________________________           |  _________________________________________
        |-| dn: hostname=appclt-2,ou=nfsClients,ou=netMounts,dc=yourorg,dc=com |          |-|volumepath=nfsserver:/vol/appdata/data1 |
        |  --------------------------------------------------------------------
        |       |
        |       |  _____________________________________________________
        |       |-| mountpoint=/opt/data2                               |
        |         | volumepath=nfsserver1:/vol/appdata/data2            |
        |         | mountoptions=rw,async,wrize=1024,rsize=1034         |
        |         | mountcomment=App data2                              |
        |         | mountdisabled=FALSE                                 |
        |          -----------------------------------------------------
        |  ____________________________________________________________________
        |-| dn: hostname=dbclt-1,ou=nfsClients,ou=netMounts,dc=yourorg,dc=com |
           --------------------------------------------------------------------
                |
                |  _____________________________________________________
                |-| mountpoint=/u1/db1                                  |
                | | volumepath=nfsserver2:/vol/appdb/db1                |
                | | mountoptions=rw,async,wrize=1024,rsize=1034         |
                | | mountcomment=App db1                                |
                | | mountdisabled=FALSE                                 |
                |  -----------------------------------------------------
                |  _____________________________________________________
                |-| mountpoint=/u1/db2                                  |
                  | volumepath=nfsserver2:/vol/appdb/db2                |
                  | mountoptions=rw,async,wrize=1024,rsize=1034         |
                  | mountcomment=App db2                                |
                  | mountdisabled=TRUE                                  |
                   -----------------------------------------------------


