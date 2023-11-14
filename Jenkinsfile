pipeline{
    agent any
        stages{
            stage("k8s"){
                steps{
                    withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'cluster', contextName: '', credentialsId: 'EKS_Creds', namespace: 'default', serverUrl: 'https://320AC5D6EE86F27E63E26B850503D5BA.gr7.eu-west-2.eks.amazonaws.com']]){
                        sh 'curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.20.5/bin/linux/amd64/kubectl"'
                        sh 'chmod u+x ./kubectl'
                        sh './kubectl get nodes'
                        sh './kubectl create -f pod.yaml'
                        sh './kubectl get pods'

}

}

}

}

}
