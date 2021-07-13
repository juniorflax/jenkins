pipeline {
  agent any
  stages {
    stage('checkName') {
      steps {
        sh 'whoami'
        sh 'hostname'
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

    stage('conditional') {
      parallel {
        stage('sleep20') {
          steps {
            sleep 20
          }
        }

        stage('msg') {
          steps {
            echo 'aguarde 20'
          }
        }

      }
    }

    stage('CONDITION') {
      steps {
        fileExists 'teste.sh'
      }
    }

  }
}