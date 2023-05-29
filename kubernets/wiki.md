
# run againest multiple pods
```
 kubectl get pods -n spr-apps -o name |grep mesos-master |xargs -I{} kubectl exec {} -n spr-apps -- mesos-master --version
```
#to get all deployments name and image:  
```
 kubectl get deployments -n spr-apps,spr-acd -o jsonpath='{range .items[*]}{@.metadata.name}{" "}{@.spec.template.spec.containers[*].image}{"\n"}{end}'|column -t 
```
#copy to local
```
kubectl cp spr-apps/rts-server-tier1-deployment-65974fff5c-qqqkz:work/2022_03_31/0000017fdfba6c30e4b06317d0407162/vad-splits/468960_490580.wav 468960_490580.wav
```
Helm:
  -> helm history publishing-prod3-tier1 -n spr-apps
  -> helm rollback publishing-prod3-tier1 129 -n spr-apps
  -> helm ls --max=10000 --all -n spr-apps
