pipeline {
	agent any
	stages {

		stage('Create K8s Cluster') {
			steps {
				withAWS(region:'us-east-1', credentials:'semo') {
					sh '''
						eksctl create cluster \
						--name capstonecluster \
						--version 1.13 \
						--nodegroup-name capstoneproj \
						--node-type t2.small \
						--nodes 2 \
						--nodes-min 1 \
						--nodes-max 3 \
						--node-ami auto \
						--region us-east-1 \
						--zones us-east-1a \
						--zones us-east-1b \
						--zones us-east-1c \
					'''
				}
			}
		}

		

		stage('Create Conf File') {
			steps {
				withAWS(region:'us-east-1', credentials:'semo') {
					sh '''
						aws eks --region us-east-1 update-kubeconfig --name capstoneproj
					'''
				}
			}
		}

	}
}
