pipeline {
  agent any
  stages {
    stage('Print On Each node') {
      parallel {
        stage('Print On Each node') {
          steps {
            timestamps() {
              echo 'Printing with timestamp'
            }

          }
        }

        stage('Printing On nodeOne') {
          steps {
            node(label: 'nodeOne') {
              sleep 5
              echo 'Printing on nodeOne'
            }

          }
        }

        stage('Printing On nodeTwo') {
          steps {
            node(label: 'nodeTwo') {
              sleep 5
              echo 'echo \'Printing on nodeTwo\''
            }

          }
        }

        stage('Printing On built-in node') {
          steps {
            node(label: 'built-in') {
              sleep 5
              echo 'echo \'Printing on built-in node\''
            }

          }
        }

      }
    }

    stage('Create file on nodeOne') {
      parallel {
        stage('Create files on each node') {
          steps {
            echo 'Creating files on node One and Two'
          }
        }

        stage('Create file on nodeTwo') {
          steps {
            node(label: 'nodeTwo') {
              writeFile(text: 'This is a text created in parallel with nodeTwo', file: 'TextCreatedWithNodeTwo.log')
            }

          }
        }

        stage('Create file on nodeOne') {
          steps {
            node(label: 'nodeOne') {
              writeFile(file: 'TextCreatedWithNodeOne.log', text: '\'This is a text created in parallel with nodeOne. Build Number:\' + %BUILD_URL%')
            }

          }
        }

      }
    }

    stage('Archive Logs') {
      parallel {
        stage('Archive Logs') {
          steps {
            echo 'Archiving logs for nodeOne and nodeTwo'
          }
        }

        stage('Archive nodeOne Log') {
          steps {
            node(label: 'nodeOne') {
              archiveArtifacts '**/*.log'
            }

          }
        }

        stage('Archive nodeTwo Log') {
          steps {
            node(label: 'nodeTwo') {
              archiveArtifacts '**/*.log'
            }

          }
        }

      }
    }

    stage('Print workspace') {
      parallel {
        stage('Print workspace') {
          steps {
            echo 'Print workspace for all nodes'
          }
        }

        stage('Print nodeOne ws') {
          steps {
            node(label: 'nodeOne') {
              sh 'ls'
            }

          }
        }

        stage('Print nodeTwo ws') {
          steps {
            node(label: 'nodeTwo') {
              sh 'ls'
            }

          }
        }

      }
    }

    stage('Clean workspace') {
      steps {
        cleanWs(cleanWhenAborted: true, cleanWhenNotBuilt: true, cleanWhenFailure: true, cleanWhenSuccess: true, cleanWhenUnstable: true, cleanupMatrixParent: true, deleteDirs: true, disableDeferredWipeout: true)
      }
    }

  }
}