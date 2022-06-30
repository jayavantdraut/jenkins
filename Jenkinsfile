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
echo "branch name  ${branch}"
if(!branch.startsWith('PR')&&index !=-1){
    barnchShort =barnchShort.substring(0,index)

}
if(branch.startsWith('PR')){
    isPr ='true'
    prNum =branch.tokenize('-')[1]
}
   def pom = readMavenPom()
   def pomVersion =pom.version;
   def buildVersion =pomVersion

   echo"pom version  ${pomVersion}"
   echo "The build number is ${env.BUILD_NUMBER}"
   def waausClassifier = "${barnchShort}b${env.BUILD_NUMBER}"

   echo "classfier ${waausClassifier}"

    configFileProvider(
           [configFile(fileId: '1291bec2-1b6b-4150-b98b-5947ee9ba2c2', variable: 'configFile')]) {

          def pro  readProperties file :"$configFile"

          echo "congi file     ${pro}"
       }



sh "mvn ${commad}"
}
