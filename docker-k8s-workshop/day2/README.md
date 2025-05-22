On Day 2, we took our Dockerized "Hello World" app from Day 1 and deployed it using Kubernetes. Here's what we did step by step:

Created a Kubernetes Deployment YAML file to define how our app should run in the cluster.

Added resource requests and limits to make sure our app gets the right amount of CPU and memory.

Defined node affinity rules and tolerations, which guide Kubernetes on where to place our Pods (on which nodes).

Used the kubectl apply -f command to apply the YAML files and create the deployment.

Verified where the pod was scheduled using:
kubectl get pods -o wide

This helped us understand how Kubernetes schedules containers, handles resources, and places pods intelligently on the right nodes.


Core Concept Questions-

Question 1- Why do we set requests and limits for CPU/memory in a production-grade product?
Answer 1- In Kubernetes, setting requests and limits for CPU and memory helps manage our app's performance and stability.
Requests: The minimum amount of CPU/memory your app needs to run smoothly.
Limits: The maximum amount it’s allowed to use.
This prevents one app from eating up all the resources and affecting others in the same cluster.

Real-World Example:
Imagine we're running an e-commerce app during a sale. If one service (say, the product page) suddenly uses too much memory due to a bug or traffic spike, it could crash the payment service. Setting limits ensures each service stays in its lane.

So, setting these values helps the system stay balanced and avoids resource hogging or unexpected crashes.

Question 2- When would a product team apply node affinity in Kubernetes?
Answer 2- Node Affinity is used when we want our app to run only on certain types of nodes in your cluster.

This is helpful when:
Some nodes are optimized for high memory
Some have GPUs
Some are reserved for sensitive or internal applications

By applying node affinity, we can guide Kubernetes to schedule pods on nodes that match specific labels.

Real-World Example:
Suppose we have a banking app with a microservice for handling sensitive data like transactions. We may want it to run only on nodes that are more secure or isolated. So we’d use node affinity to ensure it gets scheduled only on those nodes.

This improves performance, security, and compliance in real-world deployments.