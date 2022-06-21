pipeline {
    agent any
    environment{
    add :"jay"
    }
    stages {
        stage('clean') {
            steps {
                echo "clean stage branch name $env.GIT_BRANCH"
                 mvnrun("clean" ,$env.add)
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

def mvnrun(def commad,def address){
echo "printing env name $address"
sh "mvn ${commad}"
}
