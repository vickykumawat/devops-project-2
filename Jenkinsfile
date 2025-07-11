def registry = 'https://hub.docker.com/repositories/vickykumawat'
def imageName = 'ttrend'
def version   = '2.1.4'
pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.10/bin:$PATH"
}
    stages {
        stage("build"){
            steps {
                 echo "----------- build started ----------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                 echo "----------- build complted ----------"
            }
        }
        stage("test"){
            steps{
                echo "----------- unit test started ----------"
                sh 'mvn surefire-report:report'
                 echo "----------- unit test Complted ----------"
            }
        }  

         stage("Build"){
            steps{
                echo "This is the building the code"
                sh 'docker build -t ${imagename}:${version} .'
                echo "Build is Successfully"
            }
        }
        
       
}
}
