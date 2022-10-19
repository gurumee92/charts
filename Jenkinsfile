pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/gurumee92/charts.git', branch: 'main' 
      }
    }

    stage('helm chart deploy') {
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
          helm upgrade -i -f ./sample/values/develop.yaml sample ./sample
          '''
        }    
      }
    }
  }
}
