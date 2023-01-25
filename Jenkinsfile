pipeline {
  agent any

  parameters {
    string(name: 'COMPONENT', defaultValue: '', description: '')
    string(name: 'APP_VERSION', defaultValue: '', description: '')
  }

  stages {

    stage('Get App Code') {
      steps {
        dir('APP') {
          git branch: 'main', url: 'https://github.com/raghudevopsb69/${COMPONENT}'
        }
        dir('HELM') {
          git branch: 'main', url: 'https://github.com/raghudevopsb69/roboshop-helm-chart'
        }
      }
    }

    stage('Install Helm Chart') {
      steps {
        sh 'pwd'
        sh 'ls -l '
        sh 'helm upgrade -i  ${COMPONENT} ./HELM -f APP/helm-values.yml --set appVersion="${APP_VERSION}"'
      }

    }

  }

}

