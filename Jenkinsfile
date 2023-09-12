// this case requires docker image egaillardon/jmeter
// you should run this pipeline under the kubernetes, and a container named jmeter is required
// In order to execute this successfuly, please install plugins using below command
// jcli plugin install kubernetes htmlpublisher pipeline-restful-api
pipeline{
    agent {
    kubernetes {
      label 'jenkins-slave'
      defaultContainer 'jnlp'
      yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: jmeter
    image: egaillardon/jmeter
    command:
    - cat
    tty: true
"""
    }
  }
    
    stages{
        stage('test'){
            steps{
                script{
                    container('jmeter'){
                        sh 'rm -rf result && rm -rf result.jtl && jmeter -n -t src/test/resources/jmeter-e2e.jmx -l result.jtl -e -o result'
                    }
                }
            }
        }
        
        stage('report'){
            steps{
                script{
                    container('jmeter'){
                        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'result', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])
                    }
                }
            }
        }
    }
}