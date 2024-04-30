pipeline {
  agent any
  triggers{
    pollSCM('H/2 * * * *')
  }
  stages {
   stage('Build Application') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Deploy CloudHub') {
      environment {
        ANYPOINT_CREDENTIALS = credentials('5e327848-b775-4767-81cc-0c4bc94d397b')
      }
      steps {
        sh "mvn deploy -DmuleDeploy -Dcloud.env=Sandbox -DcloudhubAppName=accounts-raml-helloworld -Dmule.version=4.6.1 -Dcloud.user=${978c13c405a54ea1b86a899991857ba4
} -Dcloud.password=${bbaaE11a81AE4154A920Bf8BF0Fc3F7B}"
      }
    }
  }
}
