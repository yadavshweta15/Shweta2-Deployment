# Shweta2-Deployment
The following is an example of a Deployment. It creates a ReplicaSet to bring up three nginx Pods:
apiVersion: apps/v1

kind: Deployment

metadata:

  name: nginx-deployment

  labels:

    app: nginx

spec:

  replicas: 3

  selector:

    matchLabels:

      app: nginx

  template:

    metadata:

      labels:

        app: nginx

    spec:

      containers:

      - name: nginx

        image: nginx:1.14.2

        ports:

        - containerPort: 80
In this example:
A Deployment named nginx-deployment is created, indicated by the .metadata.name field.
The Deployment creates three replicated Pods, indicated by the .spec.replicas field
The .spec.selector field defines how the Deployment finds which Pods to manage. In this case, you select a label that is defined in the Pod template (app: nginx). However, more sophisticated selection rules are possible, as long as the Pod template itself satisfies the rule.
Create the Deployment by running the following command:

kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml
Run kubectl get deployments to check if the Deployment was created.
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   0/3     0            0           1s

When you inspect the Deployments in your cluster, the following fields are displayed:

NAME lists the names of the Deployments in the namespace.
READY displays how many replicas of the application are available to your users. It follows the pattern ready/desired.
UP-TO-DATE displays the number of replicas that have been updated to achieve the desired state.
AVAILABLE displays how many replicas of the application are available to your users.
AGE displays the amount of time that the application has been running.
