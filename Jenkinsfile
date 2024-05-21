pipeline {
<<<<<<< HEAD
agent any;
stages {
stage('Code Quality') {
steps {
sh 'echo checking code quality'
}
}
stage('Unit Tests') {
steps {
sh 'echo Testing the Applications'
}
}
stage('Build') {
steps {
sh 'echo Creating application Package'
}
}
stage('Delivery') {
steps {
sh 'echo Uploading the artifact to a repository'
}
}
stage('Deploy') {
steps {
sh 'echo Deploying the Application'
}
}
}
}
=======
    agent  any;
    stages {
        stage('Preparing the environment') {
            steps {
                sh 'python -m pip install -r requirements.txt'
            }
        }
        stage('Code Quality') {
            steps {
                sh 'python -m pylint app.py'
            }
        }
        stage('Tests') {
            steps {
                sh 'python -m pytest'
            }
        }
   
    stage('Build') {
          agent { 
            node{
              label "DockerServer"; 
              }
          }
          steps {
              sh 'docker build https://github.com/AlissonMMenezes/Chapter10.git -t chapter10:latest'
          }
      }        
      stage('Deploy') {
          agent { 
            node{
              label "DockerServer"; 
              }
          }
          steps {
              sh 'docker run -tdi -p 5000:5000 chapter10:latest'
          }
      }
    }

}

>>>>>>> 9cb3055 (first commit)
