

```bash
$ ./istioctl version
client version: 1.19.0
control plane version: 1.19.0
data plane version: 1.19.0 (1 proxies)

$ ./istioctl install
This will install the Istio 1.19.0 "default" profile (with components: Istio core, Istiod, and Ingress gateways) into the cluster. Proceed? (y/N) y
✔ Istio core installed
✔ Istiod installed
✔ Ingress gateways installed
✔ Installation complete
  Made this installation the default for injection and validation.

$ kubectl api-resources --verbs=list --namespaced -o name | xargs -t -I {} kubectl get --show-kind --ignore-not-found -n istio-system {}
kubectl get --show-kind --ignore-not-found -n istio-system configmaps
NAME                                            DATA   AGE
configmap/istio                                 2      2m51s
configmap/istio-ca-root-cert                    1      2m24s
configmap/istio-gateway-status-leader           0      2m24s
configmap/istio-leader                          0      2m24s
configmap/istio-namespace-controller-election   0      2m24s
configmap/istio-sidecar-injector                2      2m51s
configmap/kube-root-ca.crt                      1      2m53s
kubectl get --show-kind --ignore-not-found -n istio-system endpoints
NAME                             ENDPOINTS                                                        AGE
endpoints/istio-ingressgateway   10.244.0.4:15021,10.244.0.4:8080,10.244.0.4:8443                 2m23s
endpoints/istiod                 10.244.0.3:15012,10.244.0.3:15010,10.244.0.3:15017 + 1 more...   2m51s
kubectl get --show-kind --ignore-not-found -n istio-system events
kubectl get --show-kind --ignore-not-found -n istio-system limitranges
kubectl get --show-kind --ignore-not-found -n istio-system persistentvolumeclaims
kubectl get --show-kind --ignore-not-found -n istio-system pods
NAME                                        READY   STATUS    RESTARTS   AGE
pod/istio-ingressgateway-59c786768d-c2bqk   1/1     Running   0          2m23s
pod/istiod-67ffd96bdc-hd6t7                 1/1     Running   0          2m51s
kubectl get --show-kind --ignore-not-found -n istio-system podtemplates
kubectl get --show-kind --ignore-not-found -n istio-system replicationcontrollers
kubectl get --show-kind --ignore-not-found -n istio-system resourcequotas
kubectl get --show-kind --ignore-not-found -n istio-system secrets
NAME                     TYPE               DATA   AGE
secret/istio-ca-secret   istio.io/ca-root   5      2m24s
kubectl get --show-kind --ignore-not-found -n istio-system serviceaccounts
NAME                                                  SECRETS   AGE
serviceaccount/default                                0         2m53s
serviceaccount/istio-ingressgateway-service-account   0         2m23s
serviceaccount/istio-reader-service-account           0         2m52s
serviceaccount/istiod                                 0         2m52s
kubectl get --show-kind --ignore-not-found -n istio-system services
NAME                           TYPE           CLUSTER-IP     EXTERNAL-IP   PORT(S)                                      AGE
service/istio-ingressgateway   LoadBalancer   10.97.93.64    <pending>     15021:30525/TCP,80:30846/TCP,443:32518/TCP   2m23s
service/istiod                 ClusterIP      10.103.9.107   <none>        15010/TCP,15012/TCP,443/TCP,15014/TCP        2m51s
kubectl get --show-kind --ignore-not-found -n istio-system controllerrevisions.apps
kubectl get --show-kind --ignore-not-found -n istio-system daemonsets.apps
kubectl get --show-kind --ignore-not-found -n istio-system deployments.apps
NAME                                   READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/istio-ingressgateway   1/1     1            1           2m23s
deployment.apps/istiod                 1/1     1            1           2m51s
kubectl get --show-kind --ignore-not-found -n istio-system replicasets.apps
NAME                                              DESIRED   CURRENT   READY   AGE
replicaset.apps/istio-ingressgateway-59c786768d   1         1         1       2m23s
replicaset.apps/istiod-67ffd96bdc                 1         1         1       2m51s
kubectl get --show-kind --ignore-not-found -n istio-system statefulsets.apps
kubectl get --show-kind --ignore-not-found -n istio-system horizontalpodautoscalers.autoscaling
NAME                                                       REFERENCE                         TARGETS         MINPODS   MAXPODS   REPLICAS   AGE
horizontalpodautoscaler.autoscaling/istio-ingressgateway   Deployment/istio-ingressgateway   <unknown>/80%   1         5         1          2m24s
horizontalpodautoscaler.autoscaling/istiod                 Deployment/istiod                 <unknown>/80%   1         5         1          2m52s
kubectl get --show-kind --ignore-not-found -n istio-system cronjobs.batch
kubectl get --show-kind --ignore-not-found -n istio-system jobs.batch
kubectl get --show-kind --ignore-not-found -n istio-system leases.coordination.k8s.io
NAME                                                         HOLDER                    AGE
lease.coordination.k8s.io/istio-gateway-deployment-default   istiod-67ffd96bdc-hd6t7   2m25s
kubectl get --show-kind --ignore-not-found -n istio-system endpointslices.discovery.k8s.io
NAME                                                        ADDRESSTYPE   PORTS                           ENDPOINTS    AGE
endpointslice.discovery.k8s.io/istio-ingressgateway-rhj5h   IPv4          8080,8443,15021                 10.244.0.4   2m24s
endpointslice.discovery.k8s.io/istiod-dhx8v                 IPv4          15012,15017,15010 + 1 more...   10.244.0.3   2m52s
kubectl get --show-kind --ignore-not-found -n istio-system events.events.k8s.io
kubectl get --show-kind --ignore-not-found -n istio-system wasmplugins.extensions.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system istiooperators.install.istio.io
NAME                                             REVISION   STATUS   AGE
istiooperator.install.istio.io/installed-state                       115s
kubectl get --show-kind --ignore-not-found -n istio-system destinationrules.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system envoyfilters.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system gateways.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system proxyconfigs.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system serviceentries.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system sidecars.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system virtualservices.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system workloadentries.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system workloadgroups.networking.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system ingresses.networking.k8s.io
kubectl get --show-kind --ignore-not-found -n istio-system networkpolicies.networking.k8s.io
kubectl get --show-kind --ignore-not-found -n istio-system poddisruptionbudgets.policy
NAME                                              MIN AVAILABLE   MAX UNAVAILABLE   ALLOWED DISRUPTIONS   AGE
poddisruptionbudget.policy/istio-ingressgateway   1               N/A               0                     2m25s
poddisruptionbudget.policy/istiod                 1               N/A               0                     2m53s
kubectl get --show-kind --ignore-not-found -n istio-system rolebindings.rbac.authorization.k8s.io
NAME                                                             ROLE                            AGE
rolebinding.rbac.authorization.k8s.io/istio-ingressgateway-sds   Role/istio-ingressgateway-sds   2m25s
rolebinding.rbac.authorization.k8s.io/istiod                     Role/istiod                     2m53s
kubectl get --show-kind --ignore-not-found -n istio-system roles.rbac.authorization.k8s.io
NAME                                                      CREATED AT
role.rbac.authorization.k8s.io/istio-ingressgateway-sds   2023-09-16T08:29:29Z
role.rbac.authorization.k8s.io/istiod                     2023-09-16T08:29:01Z
kubectl get --show-kind --ignore-not-found -n istio-system authorizationpolicies.security.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system peerauthentications.security.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system requestauthentications.security.istio.io
kubectl get --show-kind --ignore-not-found -n istio-system csistoragecapacities.storage.k8s.io
kubectl get --show-kind --ignore-not-found -n istio-system telemetries.telemetry.istio.io
$

$ kubectl get crd
NAME                                       CREATED AT

destinationrules.networking.istio.io       2023-09-16T08:29:00Z
envoyfilters.networking.istio.io           2023-09-16T08:29:00Z
gateways.networking.istio.io               2023-09-16T08:29:00Z
proxyconfigs.networking.istio.io           2023-09-16T08:29:00Z
serviceentries.networking.istio.io         2023-09-16T08:29:00Z
sidecars.networking.istio.io               2023-09-16T08:29:00Z
virtualservices.networking.istio.io        2023-09-16T08:29:00Z
workloadentries.networking.istio.io        2023-09-16T08:29:00Z
workloadgroups.networking.istio.io         2023-09-16T08:29:00Z

authorizationpolicies.security.istio.io    2023-09-16T08:29:00Z
peerauthentications.security.istio.io      2023-09-16T08:29:00Z
requestauthentications.security.istio.io   2023-09-16T08:29:00Z

telemetries.telemetry.istio.io             2023-09-16T08:29:00Z

wasmplugins.extensions.istio.io            2023-09-16T08:29:00Z

istiooperators.install.istio.io            2023-09-16T08:29:00Z

$

```

