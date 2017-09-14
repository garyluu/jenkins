pipeline {
  agent any
  stages {
    stage('get') {
      steps {
        sh '''dockstore tool launch --config /home/ubuntu/synapse/config --entry quay.io/ga4gh-dream/dockstore-tool-synapse-get --json /home/ubuntu/synapse/gdc_dnaseq_transform_get.cwl.json
'''
      }
    }
    stage('run') {
      steps {
        sh 'dockstore workflow launch --local-entry cwl/workflows/dnaseq/transform.cwl --json transform.cwl.json'
      }
    }
    stage('check') {
      steps {
        sh 'dockstore tool launch --local-entry gdc_dnaseq_transform_checker.cwl --json gdc_dnaseq_transform_checker.cwl.json'
      }
    }
  }
}