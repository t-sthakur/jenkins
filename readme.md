# Deploy jenkins
kubectl apply -f https://raw.githubusercontent.com/brainupgrade-in/dockerk8s/main/kubernetes/lab/03-deployment/jenkins.yaml

# To cache repo for maven builds
kubectl apply -f https://raw.githubusercontent.com/brainupgrade-in/jenkins/main/examples/Kubernetes/request-logger/maven-cache.yaml