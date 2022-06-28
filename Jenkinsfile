pipeline {
    agent any
    environment{
     add = "jay"
    }
    stages {
        stage('clean') {
            steps {
                 mvnrun("clean" ,add)
            }
        }
        stage('compile') {
                    steps {
                         mvnrun("compile",add)
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
 def branch= env.BRANCH_NAME
 echo " banch name $branch"
   def pom = readMavenPom()
    echo "printing env pom version is  $pom.version"
   echo "printing env name $address"
sh "mvn ${commad}"
}
