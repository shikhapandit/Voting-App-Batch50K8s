# Commands Used
- `git clone https://github.com/ashishrpandey/example-voting-app`
- `cd /root/example-voting-app/k8s-specifications`
- `kubectl delete all --all`
- `kubectl apply -f .`
- `kubectl get all`

# My Observations
When pods were deleted. I observed the following:

1) after deleting voting pod
- the application works fine.
- Command used : `kubectl delete po vote-94849dc97-6j68f`
- this pod got deleted and a new pod got created in its place.
- Old pod - vote-94849dc97-6j68f
- New pod - vote-94849dc97-76dsj

2) after deleting worker pod
- the applications works fine.
- Command used : `kubectl delete po worker-dd46d7584-kj4sg`
- this pod got deleted and a new pod got created in its place.
- Old pod - worker-dd46d7584-kj4sg
- New pod - worker-dd46d7584-nv9bq

3)after deleting the db pod
- the voting application was not working properly.
- The votes are casted but the results are not updated.
- The results page shows equal votes of 50 % for both Cats and Dogs
- a new db pod got created in place of old db pod.
- Old pod - db-b54cd94f4-cfkt4
- New pod - db-b54cd94f4-7f7rl
- Worker pod restarted once
- when deleting this worker pod, there's no change in the frontend. Result page does not get updated.

4) Why result app stopped working after deleting db pod?
- since db pod was deleted, the connection between result pod and db pod got lost.

5) How to make result pod work again?
By deleting result pod. The connection was re-established between result pod and db pod. after deleting the existing result pod, the new result pod was created and the voting application works fine. Command used : kubectl delete po result-5d57b59f4b-ltk6f

- Old result pod - result-5d57b59f4b-ltk6f
- New result pod - result-5d57b59f4b-fzdgp
   
# Some Jargons learnt so far:-
- Docker basics
- CKAD
- Isolation
- Abstraction
- Platform
- Container
- Virtualization
- Docker Engine
- Instance
- Yum
- Image
- Docker Registry
- Port Mapping
- Microservices
- Kubectl
- Scheduler
- ETCD
- Pod
- Kubelet
- nginx
- Controller
- Replication controller
- Replica Set
- Daemon Set
- Deployment
- Rolling update
- Volumes
- Persistent Volume
- Persistent Volume Claim
- Helm
- Calico
   
