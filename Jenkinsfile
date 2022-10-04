pipeline{
    agent any
    tools {nodejs "nodejs"}
    stages{
        stage('code checkout from GitHub'){
            steps{
                git 'https://github.com/Abhilash-1201/NodeJsBoilerplateCode.git'
            }
        }
        stage('Code Quality Check via SonarQube'){
            steps{
                script{
                    def scannerHome = tool 'sonarqube-scanner';
                    withSonarQubeEnv(credentialsId: 'sonarqube_access_token'){
                        sh "${tool("sonarqube-scanner")}/bin/sonar-scanner \
                        -Dsonar.projectKey=mydemoproject \
                        -Dsonar.sources=. \
                        -Dsonar.css.node=. \
                        -Dsonar.host.url=http://3.15.224.245:9000 \
                        -Dsonar.login=sqp_52a2d63c21e2b985d727bbe69860cdc31815913f"
                        
                    }
                }
            }
        }
        stage('Install Project Dependencies'){
            steps{
                nodejs(nodeJSInstallationName: 'nodejs'){
                    sh "npm install"
                }
            }
        }
    }
}
