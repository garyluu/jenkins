pipeline {
  agent any
  stages {
    stage('synapse get') {
      steps {
        sh '''dockstore tool launch --entry quay.io/ga4gh-dream/dockstore-tool-synapse-get --json /home/ubuntu/synapse/hello_world_get.cwl.json
'''
      }
    }
  }
}