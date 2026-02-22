pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A3A5967163979D305A41D449AA8E8F64.gr7.us-east-2.eks.amazonaws.com']) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A3A5967163979D305A41D449AA8E8F64.gr7.us-east-2.eks.amazonaws.com']) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
