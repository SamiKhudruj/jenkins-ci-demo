pipeline {
  agent any
  options { timestamps(); ansiColor('xterm') }

  // Poll GitHub for new commits instead of using a webhook
  triggers { pollSCM('H/2 * * * *') }  // every ~2 minutes

  stages {

    stage('Build') {
      steps {
        echo 'TASK: Build the code.'
        echo 'TOOL: Maven (e.g., mvn -B clean package).'
      }
    }

    stage('Unit & Integration Tests') {
      steps {
        echo 'TASK: Run unit tests and integration tests.'
        echo 'TOOLS: JUnit via Maven Surefire; Postman/Newman or REST Assured for integration.'
      }
    }

    stage('Code Analysis') {
      steps {
        echo 'TASK: Static code analysis to ensure standards.'
        echo 'TOOLS: SonarQube/SonarScanner, PMD, Checkstyle.'
      }
    }

    stage('Security Scan') {
      steps {
        echo 'TASK: Scan dependencies/code for vulnerabilities.'
        echo 'TOOLS: OWASP Dependency-Check, Snyk CLI, Trivy.'
      }
    }

    stage('Deploy to Staging') {
      steps {
        echo 'TASK: Deploy app to staging environment (e.g., AWS EC2).'
        echo 'TOOLS: Ansible, Docker Compose, or Jenkins SSH steps.'
      }
    }

    stage('Integration Tests on Staging') {
      steps {
        echo 'TASK: Run integration/end-to-end tests against staging.'
        echo 'TOOLS: Cypress, Selenium, Postman/Newman.'
      }
    }

    stage('Deploy to Production') {
      steps {
        echo 'TASK: Deploy app to production (e.g., AWS EC2).'
        echo 'TOOLS: Ansible with Blue/Green or Rolling strategy; Docker.'
      }
    }
  }

  post {
    always {
      echo 'Pipeline finished. (The above prints satisfy the required 7 stages + tools.)'
    }
  }
}
