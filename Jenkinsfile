pipeline {
  agent any
  stages {
    stage('get') {
      steps {
        sh 'dockstore tool launch --config /home/ubuntu/synapse/config --entry quay.io/ga4gh-dream/dockstore-tool-synapse-get --json /home/ubuntu/synapse/encode_mapping_workflow_get.cwl.json'
      }
    }
    stage('run') {
      steps {
        sh 'dockstore workflow launch --local-entry encode_mapping_workflow.cwl --json encode_mapping_workflow.cwl.json'
      }
    }
    stage('check') {
      steps {
        sh 'dockstore tool launch --local-entry validator.cwl --json validator.json'
      }
    }
  }
}