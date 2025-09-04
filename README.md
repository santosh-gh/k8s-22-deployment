# Part 15: Deploying microservice applications in kubernetes (minikube) using ArgoCD

    Part1:   Manual Deployment (AzCLI + Docker Desktop + kubectl)  
    GitHub:  https://github.com/santosh-gh/k8s-01
    YouTube: https://youtu.be/zoJ7MMPVqFY

             - Good for learning and small projects.
             - Error-prone due to manual steps.
             - Not scalable for teams or large projects.

    Part2:   Automated Deployment (AzCLI + Docker + kubect + Azure Pipeline)
    GitHub:  https://github.com/santosh-gh/k8s-02
    YouTube: https://youtu.be/nnomaZVHg9I

            - Faster, repeatable deployments.
            - Reduces human error.
            - Integrates CI/CD best practices.

    Part3:   Automated Infra Deployment (Bicep + Azure Pipeline)
    GitHub:  https://github.com/santosh-gh/k8s-03
    YouTube: https://www.youtube.com/watch?v=5PAdDPHn8F8

    Part4:   Manual Deployment (AzCLI + Docker Desktop + Helm charts + kubectl) 
    GitHub:  https://github.com/santosh-gh/k8s-04
    YouTube: https://www.youtube.com/watch?v=VAiR3sNavh0

             - need to maintain separate files for each environment.
             - No concept of packaging/distribution.
             - no built-in rollback or release tracking.

    Part5:   Automated Deployment (AzCLI + Docker + Helm charts + kubectl + Azure Pipeline) 
    GitHub:  https://github.com/santosh-gh/k8s-04
    YouTube: https://www.youtube.com/watch?v=MnWe2KGRrxg&t=883s

             - Helm uses templates and values (values.yaml) ? same chart can deploy multiple 
               environments (dev, staging, prod) with different configs.
             - Helm packages apps as charts, which can be versioned, shared, and 
               stored in repositories (like Docker images).
             - Helm tracks releases ? easy to upgrade, rollback, and list installed versions 
               (helm upgrade, helm rollback).               
             - Helm can bundle multiple Kubernetes resources (Deployments, Services, Ingress, ConfigMaps, etc.) 
               into a single chart ? deploy everything with one command.

    Part6:   Automated Deployment (AzCLI + Docker + Helm charts + kubectl + Azure Pipeline) 
             Dynamically update the image tag in values.yaml
    GitHub:  https://github.com/santosh-gh/k8s-06
    YouTube: https://www.youtube.com/watch?v=Nx0defm8T6g&t=11s

    Part7:   Automated Deployment (AzCLI + Docker + Helm charts + kubectl + Azure Pipeline)
             Store the helm chart in ACR
             Dynamically update the image tag in values.yaml
             Dynamically update the Chart version in Chart.yaml

    GitHub:  https://github.com/santosh-gh/k8s-07
    YouTube: https://www.youtube.com/watch?v=Y3RaxSZNTaU&t=1s

    Part8:   Automated Deployment (AzCLI + Docker + Helm charts + kubectl + Azure Pipeline)
             Store the helm chart in ACR
             Dynamically update the image tag in values.yaml
             Dynamically update the Chart version in Chart.yaml
             Deploy into multiple environments (dev, test, prod) with approval gates

    GitHub:  https://github.com/santosh-gh/k8s-08
    YouTube: https://www.youtube.com/watch?v=oNysAAGijGk&t=43s

    Part9:   Manual Deployment (AzCLI + Docker + kustomize + kubectl)          
             Deploy into multiple environments (dev, test, prod) through command line

    GitHub:  https://github.com/santosh-gh/k8s-09
    YouTube: https://www.youtube.com/watch?v=Jtz1KldOPAA&t=1s

             - Overlay-based approach makes managing multiple environments (dev, staging, prod) 
               straightforward via Git branches/overlays.

    Part10:  Automated Deployment (AzCLI + Docker + kustomize + kubectl + Azure Pipeline)          
             Deploy into multiple environments (dev, test, prod) through automated pipeline

    GitHub:  https://github.com/santosh-gh/k8s-10
    YouTube: https://www.youtube.com/watch?v=m5ZXmOk0IBs&t=43s

    Part11:  Manual Deployment (AzCLI + Docker + Helm + kustomize + kubectl)          
             Deploy into multiple environments (dev, test, prod) using command line tools.

             - Helm = packaging + release mgmt (install/upgrade/rollback)
             - Kustomize = environment overlays (patches/config differences)
             - Together = scalable, reusable, environment-flexible microservice deployment strategy


    GitHub:  https://github.com/santosh-gh/k8s-11
    YouTube: https://www.youtube.com/watch?v=ZNHoZ_b85DQ&t=1s

    Part12:  Automated Deployment (AzCLI + Docker + Helm + kustomize + kubectl)
             Template First approach 
             Dynamically update the image tag in deploy.yaml         
             Deploy into multiple environments (dev, test, prod) using Azure Pipeline.

    GitHub:  https://github.com/santosh-gh/k8s-12
    YouTube: https://www.youtube.com/watch?v=qxJyTHzWG4U

    Part13:  Manual Deployment (AzCLI + Docker + Helm + kustomize + kubectl)
             Overlay First approach             
             Deploy into multiple environments (dev, test, prod) thorough commands.

    GitHub:  https://github.com/santosh-gh/k8s-13
    YouTube: https://www.youtube.com/watch?v=9uAM8FgNGmI&t=113s

    Part14:  Automated Deployment (AzCLI + Docker + Helm + kustomize + kubectl)
             Overlay First approach             
             Deploy into multiple environments (dev, test, prod) thorough Azure Pipeline.

    GitHub:  https://github.com/santosh-gh/k8s-14
    YouTube: https://www.youtube.com/watch?v=VAiR3sNavh0

    Part15: ArgoCD (Create Argo CD app using UI and Dashboard)
            Create Argo CD applications using Argo CD UI and Dashboard 

            Manual methods: Best for learning, experimentation, and very small projects.
            Automated methods: Best for production, team collaboration, and scaling.   

            kubectl: Simple no extra tools or templating engines needed.

            Helm:  Best for packaging, reusability, upgrades and rollbacks.                    
                can use reusable and ready-made chart.

            Kustomize: Best for environment-specific overlays without duplicating YAML.
                    Patch existing YAMLs for different environments.
                    Powerful when you need to tweak a vendor Helm chart

            Helm + Kustomize: Very flexible, but complex; fits for large enterprises.


            # Traditional Deployment: PUSH Approach

              - Requires the pipeline runner or command line to have cluster credentials
              - The live state may drift from the intended state
              - Rollback means re-running a previous pipeline, manually applying manifests, or 
                keeping Helm release history.
              - Usually requires custom scripting to target multiple clusters (e.g., staging, prod).

            # GitOps(ArgoCD) Deployment: PULL Approach
              
              - Runs inside the cluster and pulls changes from Git.
              - Git is the single source of truth for manifests.
                Detects drift and can automatically fix it.
              - Simply revert the Git commit, Argo syncs back to the previous state.
              - Can promote changes from dev -> test -> prod simply by managing Git branches or directories.
              - Provides a dashboard/UI showing real-time status (Healthy, OutOfSync, Degraded).

    GitHub:  https://github.com/santosh-gh/k8s-15  
    YouTube: https://www.youtube.com/watch?v=Cnt5RZ5m3l8&list=PLr6ErUeFySVug9VG73_W2MypRez_ZycWh&index=15

    Part16: ArgoCD (Create Argo CD app using UI and Dashboard, continue on Part15)
            Create Argo CD applications using Argo CD UI and Dashboard
    GitHub:  https://github.com/santosh-gh/k8s-16
    YouTube: https://www.youtube.com/watch?v=GYMY4ZQ7V9o&list=PLr6ErUeFySVug9VG73_W2MypRez_ZycWh&index=16

    Part17: ArgoCD (Create Argo CD app using manifest)
            Create Argo CD applications using manifests (CRD - Application)
    GitHub:  https://github.com/santosh-gh/k8s-17
    YouTube: https://www.youtube.com/watch?v=W-s6A61w7BI&list=PLr6ErUeFySVug9VG73_W2MypRez_ZycWh&index=17

    
    Part18: ArgoCD (Create Argo CD app using manifest)
            Create Argo CD applications using manifests
            Create Argo CD applications using manifests (CRD - ApplicationSet)
    GitHub:  https://github.com/santosh-gh/k8s-18
    YouTube: https://www.youtube.com/watch?v=GYMY4ZQ7V9o&list=PLr6ErUeFySVug9VG73_W2MypRez_ZycWh&index=16

# Architesture

![Store Architesture](aks-store-architecture.png)

    # Store front: Web application for customers to view products and place orders.
    # Product service: Shows product information.
    # Order service: Places orders.
    # RabbitMQ: Message queue for an order queue.

# Tetechnology Stack
   
    minikube
    docker desktop
    docker hub
    git hub
    kubectl
    Argo CD   

# Step 1: Start Minikube

    First, start Minikube. 

    minikube start    

# Step 2: Create a Namespace for Argo CD

    Create a separate namespace for Argo CD.

    kubectl create namespace argocd
    
# Step 3: Install Argo CD
    
    Install Argo CD

    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

    kubectl get all -n argocd

# Step 4: Expose the Argo CD Server

    To access the Argo CD web interface, expose the Argo CD server using the kubectl port-forward command:

    kubectl port-forward svc/argocd-server -n argocd 8080:443

    This command forwards the port 8080 on the local machine to port 443 of the Argo CD server.

# Step 5: Log in to Argo CD

    Browse to https://localhost:8080

    Retrieve the password using the following command:

    kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d; echo

    The output will be the name of the Argo CD server pod. Use this name as the password. The default username is admin.

# Step 6: Connect a Git Repository

    Connect a Git repository to Argo CD. This repository should contain the Kubernetes manifests for the applications you want to deploy.

    In the Argo CD web interface, Select Setting, Repository, Connect Repository

# Cretae Argo CD app
    
    - Manual (Argo CD Dash Board)
      Fill in the details like Application Name, Project, Sync Policy, and the Git repository URL.
      Specify the path within the repository where the manifests are stored.
      Choose the destination cluster and namespace.
      Click on Create to create the application.

    - Manifest (CRD - Application)

      kubectl apply -f ./argocd/applications/single-manifests.yaml -n argocd
      kubectl apply -f ./argocd/applications/single-helmchart.yaml -n argocd
      kubectl apply -f ./argocd/applications/kustomize-manifests.yaml -n argocd
      kubectl apply -f ./argocd/applications/helm-kustomize.yaml -n argocd
      kubectl apply -f ./argocd/applications/multi-environment-helmchart.yaml -n argocd

      # App of apps (deploy multiple services/apps using a root/parent argo CD manifest)
      kubectl apply -f ./apps/app-of-apps.yaml -n argocd
      kubectl apply -f ./apps-helm/app-of-apps.yaml -n argocd
      kubectl apply -f ./apps-kustomize-manifests-prod/app-of-apps.yaml -n argocd      


      # Delete the services/apps
      kubectl delete -f ./argocd/applications/single-manifests.yaml -n argocd
      kubectl delete -f ./argocd/applications/single-helmchart.yaml -n argocd
      kubectl delete -f ./argocd/applications/kustomize-manifests.yaml -n argocd
      kubectl delete -f ./argocd/applications/helm-kustomize.yaml -n argocd
      kubectl delete -f ./argocd/applications/multi-environment-helmchart.yaml -n argocd

      kubectl delete -f ./apps/app-of-apps.yaml -n argocd
      kubectl delete -f ./apps-helm/app-of-apps.yaml -n argocd  
      kubectl delete -f ./apps-kustomize-manifests-prod/app-of-apps.yaml -n argocd    

    - Manifest (CRD - ApplicationSet)

      kubectl apply -f ./appsets/single-manifests-appset.yaml
      kubectl apply -f ./appsets/multi-manifests-appset.yaml

      # Delete the services/apps
      kubectl delete -f ./appsets/single-manifests-appset.yaml
      kubectl delete -f ./appsets/multi-manifests-appset.yaml

# Step 7: Sync the Application

    After creating the application, you will see it listed on the dashboard. 

# minikube cluster

  alias k=kubectl

  k create ns single-manifests 
  k create ns multi-manifests
  k create ns single-helmchart
  k create ns multi-helmchart
  k create ns kustomize-manifests


# Docker Build and Push to Docker Hub

    # Order Service
    docker build -t order ./app/order-service 
    docker tag order:latest e880613/order:v1
    docker push e880613/order:v1

    # Product Service
    docker build -t product ./app/product-service 
    docker tag product:latest e880613/product:v1
    docker push e880613/product:v1

    # Store Front Service
    docker build -t store-front ./app/store-front 
    docker tag store-front:latest e880613/store-front:v1
    docker push e880613/store-front:v1 


kubectl apply -f ./appsets/single-manifests-appset.yaml
kubectl delete -f ./appsets/single-manifests-appset.yaml

kubectl apply -f ./appsets/multi-manifests-appset.yaml
kubectl delete -f ./appsets/multi-manifests-appset.yaml

kubectl apply -f ./appsets/multi-env-multi-manifests-appset.yaml
kubectl delete -f ./appsets/multi-env-multi-manifests-appset.yaml


kubectl apply -f ./appsets/appset.yaml
kubectl delete -f ./appsets/appset.yaml

kubectl delete -f ./appsets/multi-env-multi-manifests-appset.yaml


kubectl describe applicationsets.argoproj.io -n argocd matrix-namespaces-example


argocd appset get-items -f ./appsets/multi-manifests-appset.yaml

argocd appset template -f ./appsets/multi-manifests-appset.yaml

kubectl apply -f ./appsets/multi-manifests-appset.yaml --dry-run=client -o yaml


argocd appset get ./appsets/appset.yaml -o yaml
argocd appset get ./appsets/multi-manifests-appset.yaml

kubectl apply -f ./appsets/appset.yaml --dry-run=client -o yaml

argocd login localhost:8080 --username admin --password lA2zNg2gO0JwB693 --insecure


kubectl apply -f ./appsets/test.yaml
kubectl apply -f ./appsets/test.yaml --dry-run=client -o yaml

Install Docker
Install KinD - https://kind.sigs.k8s.io/docs/user/quick-start/

Install Flux CLI

Install Kubectl




kind --version
flux --version

# Create a KinD cluster



- This creates a single-node Kubernetes cluster inside a Docker container.
kind create cluster --name flux-demo 

kind create cluster --name flux-demo  --config=./cluster-config/config

docker ps

kubectl get nodes

kubectl cluster-info

# Install Flux in Cluster

# Bootstrap Flux in the Cluster

export GITHUB_USER=santosh-gh
export GITHUB_TOKEN=<your-token>
export GITHUB_REPO=<your-repo>

flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=$GITHUB_REPO \
  --branch=main \
  --path=clusters/flux-demo \
  --personal

# Microservice Manifests

# Define Flux Kustomization

# Flux Sync

  kubectl get kustomizations -n flux-system
  flux get kustomizations


# Verify Deployment

kind delete cluster --name demo-cluster
kind delete cluster --name flux-demo


