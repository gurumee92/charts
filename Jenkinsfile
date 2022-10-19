pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/gurumee92/charts.git', branch: 'main' 
      }
    }

    stage('gradle test') {
        agent {
            docker {
                image 'gradle:6.7-jdk11'
                reuseNode true
            }
        }
        steps {
            sh 'gradle --version'
        }
    }

    // stage('kubectl get ns') {
    //   agent { 
    //     docker {
    //       image 'rancher/kubectl:v1.23.7' 
    //     }
    //   }
    //   steps {
    //     sh '''
    //     kubectl get ns
    //     '''
    //   }
    // }
  }
}
