pipeline {
agent any
stages {

stage ("List Files") {
  steps {
sh 'pwd'
sh 'ls -ltr'
  }
}

  stage ("Build Nodejs Image") {
    steps {
      sh 'sudo docker build -t nodejs .'
      sh 'sudo docker ps'
    }
  }

  stage ("Delivery of Image to Docker Hub") {
    steps {
      sh 'sudo docker image tag nodejs bishal/nodejs:1.0'
      sh 'sudo docker push bishaldhimal/nodejs:1.0'
    }
  }

    stage ("Deployment to Kubernetes") {
    steps {
      sh 'chmod 400 susiminikube.pem'
      sh 'ls -ltr'
      sh 'scp -i susiminikube.pem -o StrictHostKeyChecking=no repo11.yml ec2-user@43.204.109.189:/home/ec2-user/'
      sh 'ssh -i susiminikube.pem ec2-user@43.204.109.189 "kubectl create -f repo11.yml"'
    }
  }


}
}
