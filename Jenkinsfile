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
      sh 'sudo docker image tag nodejs bishaldhimal/nodejs:1.0'
      sh 'sudo docker push bishaldhimal/nodejs:1.0'
    }
  }
  
    stage ("Deployment to Kubernetes") {
    steps {
      sh 'chmod 400 susiminikube.pem'
      sh 'ssh -i susiminikube.pem ec2-user@15.207.110.156 "kubectl delete pod susihttpd01"'
      sh 'ssh -i susiminikube.pem ec2-user@15.207.110.156 "kubectl run susihttpd01 --image=susigugh/httpdimg:v1.1"'
    }
  }
  
}
}


