pipeline{ 
    agent any
    
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    
    stages {
        stage('clone'){
            steps {
            git credentialsId: 'github', url:'https://github.com/javahometech/my-app'          }
        }
        
        stage('build'){
            steps {
            sh "mvn clean package"
            }
        }
        
        stage('nexus uload'){
            steps {
            nexusArtifactUploader artifacts: [[artifactId: 'ram', classifier: '', file: 'target/myweb-0.0.12.war', type: 'war']], credentialsId: '5ad67e22-4837-4910-95bc-552276637d32', groupId: 'ram', nexusUrl: '18.224.184.127:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'harsha', version: '$BUILD_ID'
            }
        }
    }
}
