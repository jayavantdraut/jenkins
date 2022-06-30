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


def branch = env.BRANCH_NAME
def barnchShort = branch.toLowerCase();
def index = barnchShort.replaceAll('[^a-z0-9-]','-').indexOf('-')
def prNum=''
def isPr ='false'
echo "branch name  {branch}"
if(!branch.startsWith('PR')&&index !=-1){
    barnchShort =barnchShort.substring(0,index)

}
if(branch.startsWith('PR')){
    isPr ='true'
    prNum =branch.tokenize('-')[1]
}
   def pom = readMavenPom()
   def pomVersion =pom.version;
   echo"pom version  ${pomVersion}"
   def waausClassifier = "${barnchShort}b${env.BULID_NUMBER}"

   echo "classfier ${waausClassifier}"

sh "mvn ${commad}"
}
