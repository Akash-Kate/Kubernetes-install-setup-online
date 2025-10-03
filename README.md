If crictl.yaml file is not present inside /etc folder of all machines in your k8s cluster please add the file present in this repo
and restart containerd once

Containerd by default cannot pull images from the local docker registry which we have created on prodcution as well as developement env
In order to pull the docker images present on the local docker registry add thses lines inside (config.toml) file present at /etc/containerd localtion
---->
[plugins."io.containerd.grpc.v1.cri".registry.mirrors."10.210.12.195:5022"]
             endpoint = ["http://10.210.12.195:5022"]

below ----> [plugins."io.containerd.grpc.v1.cri".registry.mirrors]   this line , if you do vim the line number would be 171 but dont rely on line number 
just paste the 2 lines below this registry.mirros line thats it and dont forget to restart containerd otherwise the changes wont be reflected


** calico.yaml **
This file is important manifest file for kubernetes CNI which is Container Network Interface required for pod to pod communication
To know more about this you can google and understand with examples. Without this file you cannot run your application as there will be no virtual IPS
assigned to your pods.
