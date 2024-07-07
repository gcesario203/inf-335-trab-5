pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Estágio de build') {
            steps {
                // Busca o repositório no git
                // OBS: Como a versão do git da minha máquina é mais antiga, ela ainda
                // cria por padrão a branch `master`, não precisando passar como padrão qual
                // branch será utilizada no JenkinsFile
                git 'https://github.com/gcesario203/inf-335-trab-5'

                // roda o maven e cria o .jar
                sh "mvn clean package"

            }

            /// passo que será executado no final dos passos do stage `Estágio de build`
            post {
                success {
                    /// Caminho dos testes unitários de onde será mapeado na interface do Jenkins
                    junit '**/target/surefire-reports/TEST-*.xml'

                    /// Caminho dos artefatos gerados pelo estágio de build
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}