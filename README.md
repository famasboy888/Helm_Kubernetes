# Managing nodes and applying Taints

## Taints help repel pods from being created in certain nodes

If there are error pods because they are being created in master. We can apply this to disable scheduling in master nodes:

`kubectl taint nodes master node-role.kubernetes.io/master=:NoSchedule`

To clean up all `Error` pods, we can run this:

`kubectl delete pods --field-selector status.phase=Failed`