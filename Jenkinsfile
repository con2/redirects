pipeline {
  agent any

  environment {
    PYTHONUNBUFFERED = "1"
    SKAFFOLD_DEFAULT_REPO = "harbor.con2.fi/con2"
  }

  stages {
    stage("Deploy") {
      steps {
        sh "emskaffolden -E production -- run -n infokala"
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
