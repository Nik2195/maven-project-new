pipeline
{
agent {
  label 'dev'
}
stages{
    stage('build'){
        steps {
            sh 'mvn clean package'
        }
        post {
        success {
            archiveArtifacts artifacts: '**/Targets/*.war'
                 }
             } 
    }
    

    }
}
