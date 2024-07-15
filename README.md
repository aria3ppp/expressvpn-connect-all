# expressvpn helper script

## prerequisites

```shell
expressvpn
tail
head
awk
tac
timeout
grep
```

## try all locations and connect to the first one

```shell
expressvpn ls | tail -n +5 | head -n -2 | awk '{print $1}' | tac | tac | while read loc; do expressvpn disconnect ; timeout 20s expressvpn connect $loc ; if expressvpn status | grep -q 'Connected to' ; then break; fi ; done
```

