# 1. Deploy kubia-liveness pod and see what is happening (how the pod behaves). Look at the logs of the pod. Try to make port-forward and curl the applicaion
####   kubectl apply -f  1_kubia-liveness.yaml
####   kubectl port-forward kubia-liveness 8080:8080  
####   curl localhost:8080
####   kubectl logs -f kubia-liveness
####   kubectl describe kubia-liveness

# 2. Deploy kubia-liveness2 pod and see what is happening (how the pod behaves). Look at the logs of the pod. Try to make port-forward and curl the applicaion
####   kubectl apply -f 2_kubia-liveness-probe-initial-delay.yaml.yaml
####   kubectl port-forward kubia-liveness2 8080:8080  
####   curl localhost:8080
####   kubectl logs -f kubia-liveness2
####   kubectl describe kubia-liveness2

Try to change all of liveness mechanisms in the manifest: 
- HTTP GET
- TCP SOCKET
- EXEC

# 3. Deploy kubia Replication Controller and see what is happening. Try to modify something in the manifest just to see what will happen (Replicas,Label Selector, Labels)
#### kubectl apply -f 3_kubia-rc.yaml
#### kubectl delete pods -l app=kubia
#### kubectl scale rc kubia --replicas=4
#### kubectl scale rc kubia --replicas=2
#### kubectl delete rc kubia
#### kubectl apply -f 4_kubia_pod.yaml 
#### kubectl apply -f 3_kubia-rc.yaml
#### Change the selector in Replication Controller and label in pod template
#### kubectl apply -f 3_kubia-rc.yaml
#### You will see that the old pods will stay and new pods will be creeated
#### Change the container image of the Replica Controller and deploy it again. You will see that on the current running pods nothing will happen. You will need to restart the pods in order to get the new config
#### kubectl apply -f 3_kubia-rc.yaml
#### kubectl delete pod -l app=kubia
#### kubectl delete rc kubia

# 4. Deploy kubia ReplicaSet and see what is happening. Try to modify something in the manifest just to see what will happen (Replicas, Selector, Labels)
#### kubectl apply -f 4_kubia_pod.yaml
#### kubectl apply -f 5_kubia-replicaset.yaml
#### kubectl scale rs kubia --replicas=4
#### kubectl scale rs kubia --replicas=2
#### kubectl delete pods -l app=kubia
#### Change the Selector in ReplicaSet and label in pod template (It will show an error that says that Selector and Label field is immutable). We need to delete the ReplicaSet and deploy again with new Selector and Label values
#### kubectl apply -f 5_kubia-replicaset.yaml
#### Change the container image of the Replica Set and deploy it again. You will see that on the current running pods nothing will happen. You will need to restart the pods in order to get the new config
#### kubectl apply -f 5_kubia-replicaset.yaml
#### kubectl delete pod -l app=kubia
#### kubectl delete rs kubia

# 5. Deploy kubia ReplicaSet with matchExpressions and see what is happening. Try to modify something in the manifest just to see what will happen (Replicas, Selector, Labels)
#### kubectl apply -f 6_kubia-replicaset-matchexpressions.yaml

# 6. Deploy kubia DaemonSet and see what is happening. We will see that the pods will not be scheduled because there is no disk=ssd on a nodes
#### kubectl apply -f 7_ssd-monitor-daemonset.yaml
#### kubectl label node <node_name> disk=ssd
#### kubectl get nodes -l disk=ssd
#### Delete the nodeSelector and deploy the DaemonSet again to see what will happen. The pods will be scheduled on all nodes
#### kubectl apply -f 7_ssd-monitor-daemonset.yaml




