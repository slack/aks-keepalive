# AKS Keepalive

Quick DaemonSet to configure TCP keepalives in the Linux kernel.

## Usage

1. `kubectl apply -f aks-keepalive.yaml`

`aks-keepalive` will output the current keepalive settings and then loop for 30 seconds, ensuring they are as configured in the image:

```
$ kubectl -n kube-system get po -l app=aks-keepalive
NAME                  READY     STATUS    RESTARTS   AGE
aks-keepalive-d9ds7   1/1       Running   0          13s
aks-keepalive-l5zwb   1/1       Running   0          13s
aks-keepalive-pnwq4   1/1       Running   0          13s
$ kubectl -n kube-system logs aks-keepalive-d9ds7
Current keepalive settings:
/proc/sys/net/ipv4/tcp_keepalive_time=7200
/proc/sys/net/ipv4/tcp_keepalive_intvl=75
/proc/sys/net/ipv4/tcp_keepalive_probes=9
```

## Changelog

### v0.1.0

Configure TCP keepalives to begin after 120s, repeat every 30s, fail connection after 4 failed checks (120s).
