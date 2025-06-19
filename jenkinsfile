pipeline {
  agent { 
    label 'agent-vm' 
  }

  environment {
    NOM_IMAGE = 'mon-image'
    NOM_CONTENEUR = 'mon-conteneur'
  }

  stages {
    stage('Build image conteneur'){
      steps{
        script{
          sh "docker build -t ${NOM_IMAGE} ."
        }
      }
    }
    stage('Arrêter le conteneur si existant') {
      steps{
        script{
          sh "docker stop ${NOM_CONTENEUR} || true"
        }
      }
    }
    stage('Supprimer le conteneur si existant') {
      steps{
        script{
          sh "docker rm ${NOM_CONTENEUR} || true"
        }
      }
    }
    stage('Démarrer un conteneur tout neuf depuis votre image') {
      steps{
        script{
          sh "docker run -d --name ${NOM_CONTENEUR} -p 9000:80 ${NOM_IMAGE}"
        }
      }
    }
  }
}
