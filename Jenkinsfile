pipeline {
    agent { 
        label 'docker-k8s'
    }

    environment {
        AWS_REGION = "ap-southeast-1"
        EKS_CLUSTER = "sd2195_eks_cluster"
        NAME_SPACE = "sd2195-practical-devops"
    }

    stages {
        stage ("Deploy to EKS cluster") {
            steps {
                withAWS(credentials: 'AWS_CREDS', region: "${AWS_REGION}") {
                    sh ("aws eks update-kubeconfig --name ${EKS_CLUSTER} --region ${AWS_REGION}")
                    sh ("kubectl create namespace ${NAME_SPACE}")
                    sh ("kubectl config set-context --current --namespace ${NAME_SPACE}")
                    sh ("kubectl config view --minify | grep namespace")
                    sh ("kubectl apply -f mongodb.yaml")
                    sh ("kubectl apply -f backend.yaml")
                    sh ("kubectl apply -f frontend.yaml")
                }
            }
        }
    }
}