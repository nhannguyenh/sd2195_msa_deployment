pipeline {
    agent {
        k8s {
            lable 'k8s'
        }
    }

    environment {
        AWS_REGION = "ap-southeast-1"
        EKS_CLUSTER = "sd2195_eks_cluster"
        NAME_SPACE = "sd2195_practical_devops"
    }

    stages {
        stage ("Deploy to EKS cluster") {
            steps {
                withAWS(credentials: 'AWS_CREDS', region: "${AWS_REGION}") {
                    sh ("aws eks update-kubeconfig --name ${EKS_CLUSTER} --region ${AWS_REGION}")
                    sh ("kubectl create namespace ${NAME_SPACE}")
                }
            }
        }
    }
}