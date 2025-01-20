def protectedBranches = ['main']
def projectName='Test'

pipeline {
  agent {
        label 'checkingIS38992'   
    }
    
  environment {
        DOCKER_REGISTRY="info-docker-local.jfrog.io"
        GIT_COMMIT = sh (script: 'git rev-parse --short HEAD',returnStdout: true).trim()
        PATH="${env.JAVA_HOME}/bin:${env.PATH}"
        SPRING_PROFILES_ACTIVE="test1"
        PROJECT_NAME="Test"
        KUSTOMIZE_REPO="github.com/info/kustomize.git"
        BUILD_VERSION="${env.BRANCH_NAME}-${env.GIT_COMMIT}"
     }
     
  stages {

      stage('Checkout') {
        steps {
          sh "env"
          checkout([
               $class: 'GitSCM',
               branches: [[name: '${BRANCH_NAME}']],
               doGenerateSubmoduleConfigurations: false,
               extensions: [], submoduleCfg: [],
               userRemoteConfigs: [[credentialsId: 'f718b7434342df0d', url: 'https://git.com/info/registration-service.git']]
           ])
        }
 }
