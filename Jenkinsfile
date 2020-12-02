pipeline
    {
        agent
            {
                docker { image 'maven' }
                    }
        stages {
                stage ('Checkout')
                    { 
                        steps {
                            git branch:'master', url: 'https://github.com/OWASP/Vulnerable-Web-Application.git'
                        }
                    }

                stage('Code Quality Check via SonarQube') 
                    { 
                        steps {
                            script {def scannerHome = tool 'SonarQube';
                            withSonarQubeEnv() {
                            sh "${tool("SonarQube")}/bin/ssonar-scanner \
                            -Dsonar.projectKey=OWASP \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=http://47.254.197.213:9000 \
                            -Dsonar.login=1177fe5ce8ca39ea46dbc863e8b24e9f65f4945d
                                         }
                                    }
                                }
                    }
                }
