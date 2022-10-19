pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/gurumee92/charts.git', branch: 'main' 
      }
    }

    stage('docker test') {
        steps {
            sh 'docker ps'
        }
    }

    stage('kubectl get ns') {
      agent { 
        docker {
          image 'rancher/kubectl:v1.23.7' 
        }
      }
      steps {
        sh 'kubectl version'
      }
    }
  }
}
