pipeline {
	agent any
	stages {
		stage('Create blue kubernetes cluster') {
			steps {
				withAWS(region:'us-east-1', credentials:'aws-static') {
					sh '''
						eksctl create cluster \
						--name prodalvimagreen \
						--version 1.13 \
						--nodegroup-name standard-workers \
						--node-type t2.small \
						--nodes 3 \
						--nodes-min 1 \
						--nodes-max 4 \
						--node-ami auto
					'''
				}
			}
		}
	}
}