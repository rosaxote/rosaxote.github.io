---
layout: post
title: Deploy an App to Kubernetes (Digital Ocean)
published: true
category: old
---

{{ page.title }}
================

<p class="meta">3.25.20 - San Francisco - R. Lin</p>

It might come upon you one day to host a rapidly scalable containerized app. 

Perhaps you have an application with such byzantine requirements that you have little recourse but to Dockerize it. Perhaps you received a trunkload of free cloud credits from one of the hulks trying to swipe off their competition. Whatever your circumstances, here is a guide to a path forward.


### Pre-Steps

Firstly, get yourself seated comfortably at a chair or perched at a standing desk. 

Secondly, spin up a browser and make your way to the cloud provider of your choice. In this case, I am using Digital Ocean. _If you are using something else, do not despair, I'm sure there are many nifty guides out there. Unless if you are using AWS._

Now, before we move on, if you have a Dockerized app, deploy your app to DockerHub (you can choose a public or private repo). You will use _yourDockerUsername/project_ as your image in the yaml file below. (Instructions at end of post.)

### Steps to Deployment

Login to Digital Ocean.

Click the Create button --> select Clusters. 

At last! We are at the gates of Kubernetes. Follow the instructions for setup.

On the last step, marked 'deploy the app', do take a moment to check that your cluster is available:
- In Terminal, run `kubectl --context [insert-context-name-here] get nodes`.  It should return your cluster(s). 
	- To see your current context, run `kubectl config current-context`.
- Now create a deployment.yaml file in the root of your project folder with the following template code:


```
apiVersion: v1
kind: Service
metadata:
  name: [name of your app]
spec:
  selector:
    app: [name of your app]
  ports:
  - protocol: "TCP"
    port: 6000
    targetPort: 5000
  type: LoadBalancer

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: [name of your app]
spec:
  selector:
    matchLabels:
      app: [name of your app]
  replicas: 2
  template:
    metadata:
      labels:
        app: [name of your app]
    spec:
      containers:
      - name: [name of your app]
        image: [yourDockerUsername/repoName]
        imagePullPolicy: Always
        ports:
        - containerPort: 5000
```

This YAML file tells Kubernetes what you want to run. It is telling Kubernetes the following: * Open the gates of port 6000 for this fine load-balanced service * Spin up two instances (‘Replicas’) of the container, so that if one fails ye shall have another.

`ImagePullPolicy: Always` tells Kubernetes it should always pull the latest version of your image, but this can actually get a little tricky. If your image name/tag doesn't change, it just ignores it. (More on that in Section 'Updating').

### Deploy the App

Finally, you are ready to unleash your app onto Kubernetes. Deploy the app with `kubectl --context [your-context-name-here] apply -f deployment.yaml`.
- If you’re deploying from a private Dockerhub repo, create a Secret on Kubernetes (see [instructions](https://developer.ibm.com/tutorials/accessing-dockerhub-repos-in-iks/))

Check that the pods deployed with `kubectl get pods`.

Check if the service is ready with `kubectl get service` (This may take a few minutes).

Once it’s ready, it’ll list an External-IP address, like so:

```
NAME                 TYPE           CLUSTER-IP      EXTERNAL-IP       PORT(S)          AGE
mordor-test-api    LoadBalancer   XX.XXX.XXX.XX   XX.XXX.XXX.XX   80:32101/TCP     33m
isengard-test-api   LoadBalancer   XX.XXX.XXX.XX   XX.XXX.XXX.XX   6000:32206/TCP   5m19s
kubernetes           ClusterIP      XX.XXX.XXX.XX      <none>            443/TCP          57m
```

Go to the external IP address to see if your app is running.

For example, if your app is an API, call a request, say 

`curl -X GET "http://XX.XXX.XXX.XX:6000/api" -H "Content-Type: application/json" --data '{"message": ["this house is red"]}'` 

→ This should return a response, like `{"ESTIMATE":"No"}`.

And lo and behold, if all has worked, you have a serviceable app running on Kubernetes. Pat thyself heartily for your efforts!


### When You Mess Up

If you mess up anywhere, just delete your deployment and start over. _This might not be the proper way, but it works for me._ 
- First, use `kubectl get all` to list all applications and services on the cluster.
- Next, delete the app’s Deployment and Service using kubectl delete: `kubectl delete {name of deployment} {name of service}` 
	- for example, `kubectl delete deployment.apps/mordor-test-api-deploy service/mordor-test-api-service`
	- returns: deployment "simple-deployment" deleted
	- service "simple-service" deleted   
- More here: 
[https://coreos.com/tectonic/docs/latest/tutorials/sandbox/deleting-deployment.html](https://coreos.com/tectonic/docs/latest/tutorials/sandbox/deleting-deployment.html) 



### Updating

The easiest way I've found to update is to set the image to your latest version. You need to have tagged your image with a different tag, like v1/v2/vn etc. 
Run 
`kubectl set image deployments/mordor-test-rosa-deploy mordor-api-container=op3no2/mordor-api:[version #]`

Navigate to the external IP to check that it updated.


### References

I likely would not have set up my app on Kubernetes without the help of the following links. 

Example app from Digital Ocean: 

[https://github.com/digitalocean/doks-example](https://github.com/digitalocean/doks-example)

Kubernetes instructions: 

[https://kubernetes.io/blog/2019/07/23/get-started-with-kubernetes-using-python/](https://kubernetes.io/blog/2019/07/23/get-started-with-kubernetes-using-python/) 

Deploy private DockerHub to Kubernetes:

[https://developer.ibm.com/tutorials/accessing-dockerhub-repos-in-iks/](https://developer.ibm.com/tutorials/accessing-dockerhub-repos-in-iks/ )

Deploy ML model as an API on AWS: 

[https://towardsdatascience.com/deploy-a-machine-learning-model-as-an-api-on-aws-43e92d08d05b](https://towardsdatascience.com/deploy-a-machine-learning-model-as-an-api-on-aws-43e92d08d05b)

Rolling-update without downtime:

[https://blog.sebastian-daschner.com/entries/zero-downtime-updates-kubernetes](https://blog.sebastian-daschner.com/entries/zero-downtime-updates-kubernetes)


### Docker instructions

(After creating a dockerfile) 

Inside the app/ directory, run:
`docker build -t <your-dockerhub-username>/model_api .`

Then run: `docker run -p 5000:5000 <your-dockerhub-username>/model_api`

Your application is now running in a Docker container. You can access it on http://XX.XXX.XXX.XX:5000/api or whatever port you set it to.

Run `docker push <your-dockerhub-username>/model_api` to push the image to your DockerHub account.
