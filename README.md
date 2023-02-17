# ckad-practice-questions-feb-2023

## Question: 1

> You have a Deployment object in your Kubernetes cluster that runs a containerized application. The application is
> CPU-intensive and you need to limit the amount of CPU that it can consume. Create a LimitRange object that specifies
> the maximum CPU usage for the container and a ResourceQuota object that enforces this limit for the entire namespace.
> Verify that the Deployment can still run correctly within the specified limits.

### Answer:

* kubectl create quota test-quota --hard=pods=5,cpu=500m,memory=640Mi --namespace=practice
* kubectl create deployment nginx --image=nginx --dry-run=client --port=80 -o yaml > nginx-deployment.yaml
* kubectl rollout status deployment nginx
* kubectl rollout history deployment nginx
* kubectl rollout undo deployment nginx --to-revision 1
* kubectl scale deployment nginx --replicas=1

## Question: 2

> You need to deploy a new version of your application to your Kubernetes cluster, but the deployment requires more CPU
> and memory than the previous version. Create a new Deployment object that includes a LimitRange object that specifies
> the new resource limits, and update the ResourceQuota object to allow the additional resources. How can you ensure
> that the new version of the application is deployed correctly and that it's using the new resource limits?

---

## Question: 3

> You have a pod that runs a data processing job every 1 minute. The job requires a lot of CPU and memory, and you want
> to limit the amount of resources that it can consume to avoid affecting other workloads on the cluster. How can you
> configure the pod to limit its resource usage, and ensure that it runs on a periodic schedule?

---

## Question: 4

> A pod is running on the cluster, but it's not responding. The desired behavior is to have Kubernetes restart the pod
> when an endpoint returns an HTTP 500 on the /healthcheck endpoint. The service should never send traffic to the pod
> while it is failing. Please complete the following:

* The application has an endpoint, /ready, that will indicate if it can accept traffic by returning an HTTP 200. If
  the endpoint returns an HTTP 500, the application has not yet finished initialization.
* The application has another endpoint /healthcheck that will indicate if the application is still working as expected
  by
  returning an HTTP 200. If the endpoint returns an HTTP 500 the application is no longer responsive.

---

## Question: 5

> Your application’s namespace requires a specific service account to be used.

* Create service account "limited-service"
* Update the nginx deployment to run as "limited-service" using service account
* print service account token in base64 decoded form