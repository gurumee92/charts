pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/gurumee92/charts.git', branch: 'main' 
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
        container('helm chart deploy') { 
          sh '''
          helm upgrade --install -f ./sample/values/develop.yaml sample ./sample 
          '''
        }    
      }
    }
  }
}
