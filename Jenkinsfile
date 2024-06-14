pipeline {
    agent any

    stages {
        stage('Deploy to K8S') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://95513E73D533BD69C22A6DF2FBA08FF3.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 120
                }
            }
        }
        stage('Verify Deplyment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://95513E73D533BD69C22A6DF2FBA08FF3.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}

