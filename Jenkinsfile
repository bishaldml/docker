pipeline {
agent any
stages {
  
stage ("List Files") {
steps {
sh 'pwd'
sh 'ls -ltr'
}
}
  
  stage ("Build Image") {
    steps {
      sh " docker build -t nodejs . "
    }
  }
}
}


