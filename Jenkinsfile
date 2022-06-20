pipeline {
    agent any
    stages {
        stage('clean') {
            steps {
                 echo "clean stage"
                 mvnrun("clean")
            }
        }
        stage('compile') {
                    steps {
                         echo "compile stage"
                         mvnrun("compile")
                    }
                }


    }
}

def mvnrun(def commad){
sh "mvn ${commad}"
}