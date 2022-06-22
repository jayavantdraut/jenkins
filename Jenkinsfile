pipeline {
    agent any
    environment{
    add = "jay"
    }
    stages {
        stage('clean') {
            steps {
              def pomf = readMavenPom(file: 'pom.xml')
                def ver = pom.version
                echo "clean stage pom name $ver"
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
