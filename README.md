# jenkins-s2i
Openshift jenkins custom build with s2i
```
oc apply -f ocp/imagestream.yaml
oc apply -f ocp/buildconfig.yaml
```
## Template to deploy jenkins
```
oc apply -f ocp/custom-jenkins-ephemeral.yaml
```
## Import newer jenkins image to jenkins namespace
```
oc import-image ocp-tools-4/jenkins-rhel8:v4.15.0-1723454566 --from=registry.redhat.io/ocp-tools-4/jenkins-rhel8:v4.15.0-1723454566 --confirm
```
## Set deployment with annotaion for trigger image changes
```
oc set triggers deploy/custom-jenkins --from-image=custom-jenkins:latest -c jenkins
```