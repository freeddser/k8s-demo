kubectl create -f ./
# kubectl get svc -n gocluster -o wide
NAME                       TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)       AGE       SELECTOR
gohi                       ClusterIP   10.254.142.103   <none>        9091/TCP      4m        name=gohi
traefik-ingress-service2   NodePort    10.254.90.66     <none>        80:8490/TCP   4m        k8s-app=traefik-ingress-lb2
traefik-web-ui2            ClusterIP   10.254.69.241    <none>        80/TCP        4m        k8s-app=traefik-ingress-lb2

# kubectl get pods -n gocluster -o wide
NAME                                   READY     STATUS    RESTARTS   AGE       IP             NODE
gohi-9qd78                             1/1       Running   0          4m        172.30.30.9    kube-node1
gohi-fkbzf                             1/1       Running   0          1m        172.30.59.10   kube-node2
gohi-m72r6                             1/1       Running   0          4m        172.30.92.12   kube-node3
traefik-ingress-lb2-69ff4cd985-5r29n   1/1       Running   0          4m        172.30.30.10   kube-node1
traefik-ingress-lb2-69ff4cd985-mtd7g   1/1       Running   0          4m        172.30.59.9    kube-node2

How to Scale?
#kubectl scale --replicas=5 -f gohi-controller.yaml 
# kubectl get pods -n gocluster -o wide
NAME                                   READY     STATUS    RESTARTS   AGE       IP             NODE
gohi-9qd78                             1/1       Running   0          4m        172.30.30.9    kube-node1
gohi-fkbzf                             1/1       Running   0          1m        172.30.59.10   kube-node2
gohi-m72r6                             1/1       Running   0          4m        172.30.92.12   kube-node3
gohi-md7bp                             1/1       Running   0          1m        172.30.30.11   kube-node1
gohi-xn2n8                             1/1       Running   0          4m        172.30.59.7    kube-node2
traefik-ingress-lb2-69ff4cd985-5r29n   1/1       Running   0          4m        172.30.30.10   kube-node1
traefik-ingress-lb2-69ff4cd985-mtd7g   1/1       Running   0          4m        172.30.59.9    kube-node2

monitor dashboad:
1.add hosts
2.access http://m.scpman.com:8490


goHi server:
1.add hosts
2.access http://g.scpman.com:8490