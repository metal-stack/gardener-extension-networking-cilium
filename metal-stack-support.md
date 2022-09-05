# Support for cilium at metal-stack

## Version

Must be based on v1.14.0 because we are still not at g/g 1.50+

## Configuration which worked

``ỳaml
kind: ConfigMap
  name: cilium-config
  namespace: kube-system
apiVersion: v1
data:
  agent-health-port: "9879"
  agent-not-ready-taint-key: node.cilium.io/agent-not-ready
  annotate-k8s-node: "true"
  arping-refresh-period: 30s
  auto-direct-node-routes: "false"
  bpf-ct-global-any-max: "262144"
  bpf-ct-global-tcp-max: "524288"
  bpf-lb-external-clusterip: "false"
  bpf-lb-map-max: "65536"
  bpf-map-dynamic-size-ratio: "0.0025"
  bpf-nat-global-max: "524288"
  bpf-policy-map-max: "16384"
  cgroup-root: /run/cilium/cgroupv2
  cilium-endpoint-gc-interval: 5m0s
  cluster-name: default
  cluster-pool-ipv4-cidr: 10.244.0.0/18
  cluster-pool-ipv4-mask-size: "24"
  debug: "false"
  disable-cnp-status-updates: "true"
  enable-api-rate-limit: "false"
  enable-bpf-clock-probe: "true"
  enable-endpoint-health-checking: "true"
  enable-hubble: "true"
  enable-ipv4: "true"
  enable-ipv4-masquerade: "true"
  enable-ipv6: "false"
  enable-ipv6-masquerade: "true"
  enable-k8s-terminating-endpoint: "true"
  enable-l2-neigh-discovery: "true"
  enable-metrics: "true"
  enable-policy: default
  enable-remote-node-identity: "true"
  enable-session-affinity: "true"
  enable-well-known-identities: "false"
  enable-xt-socket-fallback: "true"
  hubble-disable-tls: "false"
  hubble-listen-address: :4244
  hubble-metrics: dns drop tcp flow port-distribution icmp http
  hubble-metrics-server: :9091
  hubble-socket-path: /var/run/cilium/hubble.sock
  hubble-tls-auto-enabled: "true"
  hubble-tls-cert-file: /var/lib/cilium/tls/hubble/server.crt
  hubble-tls-client-ca-files: /var/lib/cilium/tls/hubble/client-ca.crt
  hubble-tls-key-file: /var/lib/cilium/tls/hubble/server.key
  identity-allocation-mode: crd
  install-iptables-rules: "true"
  install-no-conntrack-iptables-rules: "false"
  ipam: cluster-pool
  # This was important
  ipv4-native-routing-cidr: 10.128.240.0/22
  kube-proxy-replacement: probe
  monitor-aggregation: medium
  monitor-aggregation-flags: all
  monitor-aggregation-interval: 5s
  # This was important
  mtu: "9000" 
  nodes-gc-interval: 5m0s
  operator-api-serve-addr: 127.0.0.1:9234
  operator-prometheus-serve-addr: :6942
  preallocate-bpf-maps: "false"
  prometheus-serve-addr: :9090
  remove-cilium-node-taints: "true"
  set-cilium-is-up-condition: "true"
  sidecar-istio-proxy-image: cilium/istio_proxy
  tofqdns-enable-poller: "false"
  tunnel: disabled
  unmanaged-pod-watcher-interval: "15"

  ```
