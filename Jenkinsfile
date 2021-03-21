ef protectedBranches = ['main']
def projectName='Test'

pipeline {
  agent {
        label 'checkingIS38992'
    }
    
  environment {
        DOCKER_REGISTRY="hpeartifacts-infosight-docker-local.jfrog.io"
        GIT_COMMIT = sh (script: 'git rev-parse --short HEAD',returnStdout: true).trim()
        PATH="${env.JAVA_HOME}/bin:${env.PATH}"
        SPRING_PROFILES_ACTIVE="test1"
        PROJECT_NAME="Test"
        KUSTOMIZE_REPO="github.hpe.com/infosight/kustomize-portal.git"
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
               userRemoteConfigs: [[credentialsId: 'f78d418b7060a942df0d', url: 'https://github.hpe.com/infosight/nimble-registration-service.git']]
           ])
        }
 }
