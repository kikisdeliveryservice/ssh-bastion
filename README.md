# ssh-bastion
An ssh-bastion pod to make access to openshift clusters easy

1. Make sure that `oc` is configured to talk to the cluster
1. (Optionally configure namespace where the bastion will run: `export SSH_BASTION_NAMESPACE=openshift-ssh-bastion`.
   `openshift-ssh-bastion` is used by default.)
1. If you SSH key used during deploy of OCP is different from default one you are using, you can
    export this variable SSH_KEY_PATH to change its location. (e.g `export SSH_KEY_PATH=~/.ssh/libra.pem`).
1. Run: `curl https://raw.githubusercontent.com/eparis/ssh-bastion/master/deploy/deploy.sh | bash`
1. ssh as core to/through the bastion.
1. The bastion address can be found by running `oc get service -n openshift-ssh-bastion ssh-bastion -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'`

https://raw.githubusercontent.com/eparis/ssh-bastion/master/ssh.sh provides a simple script to automate sshing through to bastion to nodes in the cluster.
