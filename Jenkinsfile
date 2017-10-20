pipeline {
  agent any
  stages {
    stage('get') {
      steps {
        deleteDir()
        sh 'pip list'
        sh 'dockstore -v'
        sh 'dockstore tool launch --config /home/ubuntu/synapse/config --entry quay.io/ga4gh-dream/dockstore-tool-synapse-get --json /home/ubuntu/synapse/knoweng_gene_prioritization_get.cwl.json'
      }
    }
    stage('run') {
      steps {
        sh 'dockstore workflow launch --local-entry gp_workflow.cwl --yaml gp_workflow_job.yml'
      }
    }
    stage('check') {
      steps {
        sh 'dockstore tool launch --local-entry check_results.cwl --yaml check_results_job.yml'
      }
    }
    stage('grep') {
      steps {
        sh 'cat results.json | grep overall'
      }
    }
  }
}