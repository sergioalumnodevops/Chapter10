pipeline {
    agent any
    stages {

        stage('Preparando el entorno') {
            agent { 
            node{
              label "ob1"; 
              }
          }
            steps {
                sh 'whoami'
                sh 'echo POR FAVOR !!!!!! fijaos en este dato'
                sh 'hostname'
                sh 'python3 -m pip install -r requirements.txt'
            }
        }
        stage('Calidad de código') {
            agent {
                node {
                    label "ob1";
                }
            }
            steps {
                 sh 'whoami'
                sh 'hostname'
                sh 'python3 -m pylint app.py'
            }
        }
        stage('Tests') {
             agent {
                node {
                    label "ob1";
                }
            }           
            steps {
                sh 'whoami'
                sh 'hostname'
                sh 'python3 -m pytest'
            }
        }
   
    stage('construcción del artefacto') {
          agent { 
            node{
              label "ob2"; 
              }
          }
          steps {
              sh 'whoami'
              sh 'hostname'
              sh 'docker build https://github.com/sergioalumnodevops/Chapter10.git -t sergiojenkins:latest'
          }
      }        
      stage('Despliegue') {
          agent { 
            node{
              label "ob2"; 
              }
          }
          steps {
              sh 'whoami'
              sh ' echo si el dato anterior es root ... NOS HEMOS VUELTO LOCOS Y VAMOS A MORIR TODOS!!!!!!'
              sh 'hostname'
              sh 'docker run --name sergioapp -tdi -p 5000:5000 sergiolatest:latest'
          }
      }
    }

}


