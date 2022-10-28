In order to create the config files to the k8s master we do: 

    kubectl apply -f client-pod.yml
    kubectl apply -f client-node-port.yml

Note that the 'apply' command is how we make any changes to the configuration to our k8s cluster.

To get detailed information about an object in our cluster we can use the 'describe' command:

    kubectl describe <object type> <object name>

Note! We can omit <object name> and then we will be getting all the information about all the different objects with the specified object type

 ## Kubernetes object

  - Pods 
  Run one or more closely related containers    
  - Services
  Sets up networking in a Kubernetes Cluster
  - Deployment
  Maintains a set of identical pods, ensuring that they have
  the correct config and that the right number exists. So, basically a "Deployment" object maintains a set of identical pods (it can be 1 Pod, 2 Pods or more...) and the deployment is going to constantly work to make sure that every single Pod  in its 'set' that is supposed to manage is always running the correct configuration and is always in a runnable state.
  A Deployment is kinda similar to the Pod object. Even though a Deployment contains a set of Pods, in the end of the day it is essentially used to run containers for our application. 

## Differences between Pod and Deployment

# Pod 
    - Runs a single set of containers
    - Good for one-off development purposes. Usually when we have a very signle container or a very small group of containers that we want to run. 
    - Rarely used directly in production because of the limitation around being able to update its configuration.

# Deployment
    - Runs a set of identical Pods(one or more).
    - Monitors the state of each Pod, updating as necessary. Deployments is going to watch the configuration of each Pod, it is going to make sure that every Pod is running the container successfully inside of it. If any Pod happens to crash for any reason, the Deployment is going to automatically going to restart that Pod or completely recreate it in a fresh new state. 
    - Good for development purposes.
    - Good for production.

# Deployment object creation:    
When we create a Deployment object, it is going to have something thats called a Pod template. 
# Pod Template
A Pod Template is essentially a little configuration block, that instructs how Pod/Pods should look like created by the Deployment.
 Usually in the Pod template we specify as said above how a Pod should look like but also the number of containers, name, port and the image which the containers are goign to get created. 
 Note! With deployment we can change any piece of configuration tied to a Pod even when the Pod is up and running.

 # Delete an existing kubernetes object

    kubectl delete -f <config-file>

