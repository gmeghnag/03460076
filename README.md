# 03460076

Run the reproducer (it requires to have OpenShift GitOps installed):

1. Create the resources:
~~~
oc apply -k https://github.com/gmeghnag/03460076
~~~

2. Bind the ClusterRole to the ServiceAccount:
~~~
oc adm policy add-cluster-role-to-user test-clusterrole -z test-sa -n reproducer-03460076
~~~

3. See the `Subjects` field reported in the `DIFF` tab of the `ClusterRoleBinding` resource:
~~~
https://openshift-gitops-server-openshift-gitops.apps.<CLUSTERNAME>.<DOMAIN_NAME>/applications/openshift-gitops/reproducer-03460076?view=tree&conditions=false&node=rbac.authorization.k8s.io%2FClusterRoleBinding%2F%2Ftest-clusterrole%2F0&resource=
~~~