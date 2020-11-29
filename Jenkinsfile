pipeline {
  agent any

  environment {
    PYTHONUNBUFFERED = "1"
  }

  stages {
    stage("Deploy") {
      steps {
        sh "emskaffolden -E production -- run -n redirects"
      }
    }
  }

  post {
    always {
      archiveArtifacts "build.json"
      archiveArtifacts "kubernetes/template.compiled.yaml"
    }
  }
}
