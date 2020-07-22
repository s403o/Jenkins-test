pipeline {
  agent any
  stages {
    stage('k8s') {
      steps {
        withAWS(region: 'us-west-2', credentials: 'ecr_credentials') {
          sh '''
  eksctl create cluster 
  --name capstoneproj 
  --version 1.13 
  --nodegroup-name standard-workers 
  --node-type t2.small 
  --nodes 2 
  --nodes-min 1 
  --nodes-max 3 
  --node-ami auto 
  --region us-west-2 
  --zones us-east-1a 
  --zones us-east-1b 
  --zones us-east-1c 
'''
        }

      }
    }

  }
}