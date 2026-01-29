
def k8sPodYaml = """
apiVersion: v1
kind: Pod
spec:
    serviceAccountName: airflow-common
    containers:
    -   name: python
        image: 087473112489.dkr.ecr.us-east-1.amazonaws.com/astronomer-jenkins:python-0.3.0
        command: ['cat']
        tty: true
        resources:
            requests:
                cpu: 1000m
                memory: 4Gi
            limits:
                memory: 6Gi
"""

pipeline {
    agent none
    stages {
        stage ('test') {
            agent {
                kubernetes {
                    yaml k8sPodYaml
                }
            }
            steps {
                sh "python -c \"print('hello')\""
            }
        }
    }
}
