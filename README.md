# tincvpn-cookiecutter

This playbook can be used to generate the required configuration to configure a
tinc vpn between a host and a guest. The "host" is the machine that is the
"main" node, to which a "guest" connects to.

# How to use

## On the host node

```
$ make install-tinc
$ make copy-to-host
$ make generate-keys
```

## On the guest node

```
$ make install-tinc
$ make copy-to-guest
$ make generate-keys
```

## Exchange keys between the master and the slaves:

a) On guest machine, copy its public key to the host machine:
```
$ scp /etc/tinc/netname/hosts/guest user@host_ip:/tmp
```

b) On host machine, copy the public key of step a into /etc/tinc/netname/hosts:
```
$ cp /tmp/guest /etc/tinc/netname/hosts
```

c) On host machine, copy its public key to the guest machine:
```
$ scp /etc/tinc/netname/hosts/host user@guest_ip:/tmp
```

d) On guest, copy host's file to the appropriate location:
```
$ cp /tmp/host /etc/tinc/netname/hosts
```

## Enable and start the service (on the host, then the guest)

```
$ sudo systemctl enable tinc
$ sudo systemctl start tinc
```

# References

<https://tiagopr.nl/posts/create_a_peer_to_peer_vpn_with_tinc_vpn>
