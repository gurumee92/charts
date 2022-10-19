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
        kubernetes {
              containerTemplate {
                name 'helm'
                image 'lachlanevenson/k8s-helm:v3.9.4'
                ttyEnabled true
                command 'cat'
          }
        }
      }
            
      steps {
        container('helm') { 
          sh '''
          pwd
          helm version
          '''
        }    
      }
    }
  }
}
