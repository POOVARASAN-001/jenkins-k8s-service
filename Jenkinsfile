
pipeline {
    agent any

    environment {
        KUBECTL = 'D:\\DockerApp\\resources\\bin\\kubectl.exe'
        KUBECONFIG = 'C:\\Users\\POOVARASAN\\.kube\\config'
    }

    stages {
        stage('Deploy Application') {
            steps {
                bat '"%KUBECTL%" apply -f deployment.yaml'
                bat '"%KUBECTL%" apply -f service.yaml'
            }
        }

        stage('Verify Service') {
            steps {
                bat '"%KUBECTL%" rollout status deployment/web-service-app --timeout=120s'
                bat '"%KUBECTL%" get service web-service'
                bat '"%KUBECTL%" get pods -l app=web-service-app'
            }
        }
    }
}
