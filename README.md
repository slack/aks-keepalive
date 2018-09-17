# AKS Keepalive

Quick DaemonSet to configure TCP keepalives in the Linux kernel.

## Usage

1. `kubectl apply -f aks-keepalive.yaml`

## Changelog

### v0.1.0

Configure TCP keepalives to begin after 120s, repeat every 30s, fail connection after 4 failed checks (120s).
