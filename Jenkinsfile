pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'gradle build'
        bat 'gradle javadoc'
        archiveArtifacts 'build/libs/**/*.jar'
        archiveArtifacts 'build/docs/javadoc/**'
        junit 'build/test-results/test/*.xml'
      }
    }

    stage('Mail Notification') {
      steps {
        mail(subject: 'Test Jenkins', body: 'heloo', to: 'ga_lagrid@esi.dz', cc: 'ga_goumeida@esi.dz', replyTo: 'ga_lagrid@esi.dz')
      }
    }

    stage('Code Analysis') {
      steps {
        withSonarQubeEnv 'sonar'
        bat 'C:\\Users\\asmaa lagrid\\Downloads\\SIL1\\OUTIL\\gradle-6.0.1\\bin\\gradle sonarQube'
      }
    }

  }
}