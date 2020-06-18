pipeline {
   agent any

   stages {
      stage('SCM') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/sri008/maven-multi-module-example.git'
         }
      }
      stage('Build Clean') {
         steps {
            sh label: '', script: '/opt/maven/bin/mvn clean package -Dmaven.test.skip=true'
         }
      }
      stage('Release') {
         steps {
            sh '/opt/maven/bin/mvn --batch-mode release:clean release:prepare release:perform -DreleseVersion=1.0 -DevelopmentVersion=1.1-SNAPSHOT'
         }
      }
      stage('Update Rel') {
         steps {
            sh 'git push https://sri008:kiri567sri@github.com/sri008/maven-multi-module-example.git HEAD:master'
         }
      }
   }
}
