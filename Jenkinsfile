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
              writeFile(file: 'TextCreatedWithNodeOne.log', text: 'This is a text created in parallel with nodeOne')
            }

          }
        }

      }
    }

    stage('Printing workspace content') {
      steps {
        sh 'sh ls'
      }
    }

  }
}