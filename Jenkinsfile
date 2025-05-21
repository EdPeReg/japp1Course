pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/EdPeReg/japp1Course', branch: 'master', credentialsId: '78388747-3d60-459c-ac56-510894ffd17d')
        sh '''sudo docker build -t dardo1818/buildrepo1:latest .
sudo docker push dardo1818/buildrepo1:latest'''
      }
    }

    stage('ParDeploy') {
      parallel {
        stage('ParDeploy') {
          steps {
            sh 'sudo docker run -d -p 7777:8080 dardo1818/buildrepo1:latest .'
          }
        }

        stage('DeployDev') {
          steps {
            echo 'deplo dev'
          }
        }

      }
    }

    stage('DeploProd') {
      steps {
        echo 'Deploying'
      }
    }

  }
}