pipeline {
    agent any
    stages {
        stage('clean') {
            steps {
                echo "clean stage branch name $env.GIT_BRANCH"
                 mvnrun("clean")
            }
        }
        stage('compile') {
                    steps {
                         echo "compile stage global variable $env.owner"
                         mvnrun("compile")
                    }
                }


    }
}

def mvnrun(def commad){
sh "mvn ${commad}"
}
