pipeline {
    agent any

    stages {
        stage('Deploy RBAC to Kubernetes') {
            steps {
                withKubeCredentials(
                    kubectlCredentials: [
                        [
                            caCertificate: '''MIIC/jCCAeagAwIBAgIBADANBgkqhkiG9w0BAQsFADAVMRMwEQYDVQQDEwprdWJlcm5ldGVzMB4XDTIzMTExMzEwNTkxM1oXDTMzMTExMDEwNTkxM1owFTETMBEGA1UEAxMKa3ViZXJuZXRlczCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAJyuXRP/FtvegqWeNwqsG1prAZotPRcXJMgMZ3ija3IfnSbQXfER8+f1jJqwl2cu6iqxuvchXgwryJfIqC58WeGrYow+3TcE7KB7PATFQutzGqMrKVDh9jhmuYqdN1iPTSZa1mQGU1Wcomj57mVma1cVU1Z+L9talKGcKPyViI9SQT3fg6L+zeoSgiZcAXGtyvI8gKzUwv/Nwwzv3NpuetqUaTiKOO7KeoRx2zbzkZyJWnV4oiERnFkfYhKDTVqVw/Lnxb6VPYYlb4SwnOAdi6NrJYg4JVhMqLXUPOK2nppG+0jnVLg826qD4Tiee17YH2zCm/VRz1f7uD5jiXe6Ee0CAwEAAaNZMFcwDgYDVR0PAQH/BAQDAgKkMA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYEFC6CXexx6jDuEOnDGxxPRZUhbLEuMBUGA1UdEQQOMAyCCmt1YmVybmV0ZXMwDQYJKoZIhvcNAQELBQADggEBAIhFw9ax1RXDrpyZ8+fzetCptIO1T2AJscXTUaugaVMxnCO2aeohTFxF/fxueyxn4ltHRF0BaMy8youhbv6ztimfcqS+yH2nixflEBuThBFJKDh8PCGK+318o+81hR9tWlIBCeVObD+G/EHXwBclUOwWitU6VTTy+51FIfUg9HCueFWRdXafjiU2QRCtpkKt2sISi2o1DawrJfK91yo6mVSVCQMhJLljIROfL630A34TI8TxO//X+PZ7TfbhX/JysDI/xSnqmR5mAHKvmYgPwYbFJTcoUDRgATufs7XX0iQPuSdu5I8nS+CSIYzvAvhR29hEkDN4RLR/1tAIqEPsGzM=''',
                            clusterName: 'arn:aws:eks:eu-west-2:296014590943:cluster/cluster',
                            contextName: 'arn:aws:eks:eu-west-2:296014590943:cluster/cluster',
                            credentialsId: 'secret_text',
                            namespace: '',
                            serverUrl: 'https://320AC5D6EE86F27E63E26B850503D5BA.gr7.eu-west-2.eks.amazonaws.com'
                        ]
                    ]
                ) {
                    sh './kubectl apply -f run.yaml'
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
