# label-studio-integration
Label Studio Integration with Open Data Hub


### Installation

1. `git clone git@github.com:opendatahub-io-contrib/label-studio-integration.git`  

2. `cd label-studio-integration`  

3. `cd label-studio`

4. `oc apply -f deploy/openshift/postgres`  

5. Wait for postgres pod to be up and running. Once the pod is running grab the pod ip and enter it as the `postgres-host` in the deploy/openshift/labelstudio/deployment.yaml as follows (Note: this is currently a workaround)
```
- name: POSTGRE_HOST
  value: [127.0.0.1]  //replace ip with the pod ip of the postgres pod
```

6. `oc apply -f deploy/openshift/nginx`

7. `oc apply -f deploy/openshift/postgres`



TODOs:
1. Fix the postgres deployment so that labelstudio can discover postgres using a `hostname` rather than the static ip of the pod. This is a temp workaround.
2. Implement readycheck for the postgres deployment.
3. Implement a livenessprobe for the labelstudio route
