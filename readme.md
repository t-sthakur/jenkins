# Deploy jenkins
kubectl apply -f https://raw.githubusercontent.com/brainupgrade-in/dockerk8s/main/kubernetes/lab/03-deployment/jenkins.yaml

# Deploy docker agent
kubectl apply -f https://raw.githubusercontent.com/brainupgrade-in/dockerk8s/main/kubernetes/lab/03-deployment/jenkins-agent.yaml

# To cache repo for maven builds
kubectl apply -f https://raw.githubusercontent.com/brainupgrade-in/jenkins/main/examples/Kubernetes/request-logger/maven-cache.yaml

# To run Junit tests
Add pipeline project https://github.com/jenkinsci/performance-plugin 

# Sonar Qube
withSonaryQubeEnv('sonarqube'){
    sh ''' 
    $SCANNER_HOME/bin/sonar-scanner \ 
     -Dsonar.projectName=${env.JOB_NAME} \ 
     -Dsonar.java.binaries=. \ 
      -Dsonar.projectKey=${env.JOB_NAME}
    '''
}

Update Jenkins settins and tools accordingly

# OWASP
dependencyCheck additionalArguments: '', odcInstallation: 'owasp-dc' dependencyCheckPublisher patter: '**/dependency-check-report.xml'

Specify in Jenkins tools: owasp-dc and use dependency-check as installation options

# References
https://github.com/fabric8io/fabric8-jenkinsfile-library/
https://github.com/cloudogu/jenkinsfiles
https://github.com/hoto/jenkinsfile-examples/blob/master/jenkinsfiles/050-shared-library-where-is-it-cloned.groovy