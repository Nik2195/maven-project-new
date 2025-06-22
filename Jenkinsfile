pipeline
{
agent {
  label 'dev'
}
parameters{
    string defaultValue: 'richard', name: 'LASTNAME' 
}
environment{
    NAME = 'nikhil'
}

tools {
  maven 'maven'
}

stages{
    stage('build'){
        steps {
            sh 'mvn clean package'
            echo "welcome $NAME ${params.LASTNAME}"
        }
         
    }
    stage('test'){
        parallel{
            stage('TESTA'){
                steps{
                    echo 'Test A'
                }
            }
            stage('TESTB'){
                steps{
                    echo 'testB'
                }
            }    
post {
        success {
            archiveArtifacts artifacts: '**/target/*.war'
                 }
             }
        }
    }

    }
}
