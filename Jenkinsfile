pipeline
{
agent {
  label 'dev'
}
parameters{
    choice choices: ['dev', 'prod'], name: 'select_env'
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
            sh 'mvn clean package -DskipTests=true'
        }
         
    }
    stage('test'){
        parallel{
            stage('TESTA'){
                agent {label 'dev'}
                steps{
                    echo 'Test A'
                    sh 'mvn test'
                }
            }
            stage('TESTB'){
                agent {label 'dev'}
                steps{
                    echo 'testB'
                    sh 'mvn test'
                }
            } 
        }       
        post {
        success {
            dir("webapp/target/")
            {
            stash name: "maven-build", includes: "*.war"
            }
                 }
             }
    }
    stage('deploy')
    {
        when {expression {params.select_environment == 'dev'}
        beforeAgent true}
        agent { label 'dev' }
        steps{
            dir("/var/www/html")
            {
                unstash "maven-build"
            }
            sh"""
            cd /var/wwww/html
            jar -xvf webapp.war
            """
        }
    }
    
    
    
    }
}
