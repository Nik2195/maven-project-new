pipeline
{
agent {
  label 'dev'
}
parameter{
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
            echo 'welcome $NAME ${params.LASTNAME}'
        }
        post {
        success {
            archiveArtifacts artifacts: '**/target/*.war'
                 }
             } 
    }
    

    }
}
