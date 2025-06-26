pipeline {
    agent any

    stages {
        stage('Depoly to K8') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://B041452B2D889023DA9AE93B9A790FF7.yl4.us-west-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                   
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://B041452B2D889023DA9AE93B9A790FF7.yl4.us-west-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
