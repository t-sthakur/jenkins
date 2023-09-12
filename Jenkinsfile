pipeline{
    agent {
    kubernetes {
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
                        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'result', reportFiles: 'result.jtl', reportName: 'JMeter Report', reportTitles: ''])
                    }
                }
            }
        }
    }
}