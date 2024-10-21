pipeline {
    agent any

    stages {
        stage('Depoloy To K8') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' eks-5', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CDA181E3FD9DFCF492FE298233842A0A.gr7.us-west-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' eks-5', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CDA181E3FD9DFCF492FE298233842A0A.gr7.us-west-1.eks.amazonaws.com']]) {
                    sh 'kubectl get svc -n webapps'
                }
            }
        }
    }
}
