pipeline {
    agent any

    environment {
        AWS-REGION = "ap-southeast-1"
        EKS_CLUSTER = "sd2195_eks_cluster"
        NAME_SPACE = "sd2195_practical_devops"
    }

    stages {
        stage ("Deploy to EKS cluster") {
            steps {
                withAWS(credentials: 'AWS-CREDS', region: ${AWS_REGION}) {
                    sh ("aws eks update-kubeconfig --name ${EKS_CLUSTER} --region ${AWS_REGION}")
                    sh ("kubectl create namespace ${NAME_SPACE}")
                }
            }
        }
    }
}