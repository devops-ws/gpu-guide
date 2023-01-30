# gpu-guide

## 安装 NVIDIA 容器运行时
```shell
hd i nvidia-docker2
```

## 安装 GPU Operator
```shell
helm repo add nvidia https://nvidia.github.io/gpu-operator
helm repo update
helm install gpu-operator nvidia/gpu-operator -n gpu-operator-resources --set toolkit.version=1.6.0-centos7
```

## 测试
```shell
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Pod
metadata:
   name: dcgmproftester
spec:
   restartPolicy: OnFailure
   containers:
   - name: dcgmproftester
     image: nvcr.io/nvidia/k8s/cuda-sample:vectoradd-cuda10.2
     resources:
      limits:
         nvidia.com/gpu: 1
EOF
```

## FAQ
* `version `GLIBC_2.27' not found`
  * 部分驱动有问题，可以通过指定驱动版本解决。详情参考[这里](https://github.com/NVIDIA/gpu-operator/issues/72).

## 参考
* https://github.com/kubesphere/website/blob/4a98ae47cb26307899936a26c972dcb30ebd126d/content/zh/blogs/GPU-Operator.md
