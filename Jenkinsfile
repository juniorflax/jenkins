pipeline {
  agent any
  stages {
    stage('checkDados') {
      parallel {
        stage('checkWhoami') {
          steps {
            sh 'whoami'
          }
        }

        stage('checkHostname') {
          steps {
            sh 'hostname'
          }
        }

        stage('checkIP') {
          steps {
            sh 'ifconfig'
          }
        }

      }
    }

    stage('checkService') {
      steps {
        sh '''result=`ps -ef | grep jenkins | grep -v grep`
if [ -z "$result" ];
then
       echo "NOK"
       exit
else
       echo "OK"
       exit 0
fi'''
      }
    }

    stage('msg') {
      parallel {
        stage('msg') {
          steps {
            echo 'erro calculado'
          }
        }

        stage('CheckFake') {
          steps {
            sh '''result=`ps -ef | grep naoexiste | grep -v grep`
if [ -z "$result" ];
then
       echo "NOK"
       exit
else
       echo "OK"
       exit 0
fi'''
          }
        }

      }
    }

    stage('CheckFile') {
      steps {
        validateDeclarativePipeline '/root/jenkinsteste.txt'
      }
    }

  }
}