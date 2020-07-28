# kubernetes-cluster

To start the cluster, make sure `vagrant` and `ansible` is installed, and then:

    $ vagrant up

This will start a 3 node cluster on your host machine.

To ssh into your master node type:

    $ vagrant ssh k8s-master

Now you can use the `kubectl` command like below.

```
vagrant@k8s-master:~$ kubectl get nodes -o wide
NAME         STATUS   ROLES    AGE   VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
k8s-master   Ready    master   33m   v1.18.6   10.0.0.10     <none>        Ubuntu 16.04.6 LTS   4.4.0-186-generic   docker://19.3.12
node-1       Ready    <none>   29m   v1.18.6   10.0.0.11     <none>        Ubuntu 16.04.6 LTS   4.4.0-186-generic   docker://19.3.12
node-2       Ready    <none>   26m   v1.18.6   10.0.0.12     <none>        Ubuntu 16.04.6 LTS   4.4.0-186-generic   docker://19.3.12

```
