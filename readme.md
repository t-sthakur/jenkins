# Deploy jenkins
kubectl apply -f https://raw.githubusercontent.com/brainupgrade-in/dockerk8s/main/kubernetes/lab/03-deployment/jenkins.yaml

# To cache repo for maven builds
kubectl apply -f https://raw.githubusercontent.com/brainupgrade-in/jenkins/main/examples/Kubernetes/request-logger/maven-cache.yaml

# To run Junit tests
Add pipeline project https://github.com/jenkinsci/performance-plugin 


# References
https://github.com/fabric8io/fabric8-jenkinsfile-library/
https://github.com/cloudogu/jenkinsfiles
https://github.com/hoto/jenkinsfile-examples/blob/master/jenkinsfiles/050-shared-library-where-is-it-cloned.groovy