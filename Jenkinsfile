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
        ANYPOINT_CREDENTIALS = credentials('bb589f35-2529-483e-bb8d-8d94f14c8bee')
      }
      steps {
        sh "mvn deploy -DmuleDeploy -Dcloud.env=Sandbox -DcloudhubAppName=accounts-raml-helloworld -Dmule.version=4.6.1 -Dcloud.user=${ANYPOINT_CREDENTIALS_USR} -Dcloud.password=${ANYPOINT_CREDENTIALS_PSW}"
      }
    }
  }
}
