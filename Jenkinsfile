pipeline{
    agent any

    tools {
        mave "M3"
    }

    stages{
        stage('Stage'){
            steps {
            // damos fetch do nosso código no git
            git 'https://github.com/gcesario203/inf-335-trab-5'

            // executa o maven e 'limpa' o build anterior?
            sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }

        post {
            success {
                junit '**/target/sunfire-reports/TEST-*.xml'
                archiveArtifacts 'target/*.jar'
            }
        }
    }
}