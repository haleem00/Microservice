pipeline {
    agent any

    stages {
        
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'my-cluster1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://1C9714EB241EA00328DF3A8944DFC80B.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                 }
            }
        }
        
        stage('verify Deployment') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: 'my-cluster1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://1C9714EB241EA00328DF3A8944DFC80B.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                 }
            }
        }
        
    }
}
