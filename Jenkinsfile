 1 pipeline {
  2    agent any
  3 
  4    stages {
  5       stage('pull code') {
  6           steps {
  7             checkout([$class: 'GitSCM', branches: [[name: '*/${master}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId    : 'a8e22755-a0e8-4075-8429-6ac0f52d74f9', url: 'https://github.com/dqwtest/community.git']]])
  8           }
  9       }
 10       stage('build project') {
 11           steps {
 12             sh label: '', script: 'mvn clean package'
 13           }
 14       }
 15       stage('publish project') {
 16           steps {
 17             deploy adapters: [tomcat8(credentialsId: '281145a3-9ff5-4245-b756-af81aa2acfab', path: '', url: 'http://47.98.200.72:8080/')], contextPath: null, war: 'target/*.war'
 18           }
 19       }
 20    }
 21 }
 22 
