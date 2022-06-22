pipeline {
    agent any
    environment{
         IMAGE = readMavenPom().getArtifactId()
    VERSION = readMavenPom().getVersion()
     add = "jay"
    }
    stages {
        stage('clean') {
            steps {
               pom.version
                echo "clean stage pom name $VERSION"
                 mvnrun("clean" ,add)
            }
        }
        stage('compile') {
                    steps {
                         echo "compile stage global variable $env.owner"
                         mvnrun("compile")
                    }
                }

    }
    post{

        success{
            echo "pipeline run success"
        }

       failure{
       echo "pipeline failure "
       }
    }
}

def mvnrun(def commad,def address){
echo "printing env name $address"
sh "mvn ${commad}"
}
