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

  }
}