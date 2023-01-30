# gpu-guide


```shell
helm repo add nvidia https://nvidia.github.io/gpu-operator
helm repo update
helm install gpu-operator nvidia/gpu-operator -n gpu-operator-resources --set toolkit.version=1.6.0-centos7
```

https://github.com/kubesphere/website/blob/4a98ae47cb26307899936a26c972dcb30ebd126d/content/zh/blogs/GPU-Operator.md
