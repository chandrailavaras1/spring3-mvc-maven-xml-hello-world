pipeline {
    agent any
    tools {
        maven "Maven"
        jdk "JDK17"
    }
    environment{
        TOMCAT_CREDS = credentials ("tomcat_creds")
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "34.16.179.184:8081"
        NEXUS_REPO = "chandu-repo"
    }
    stages{
        stage("Build"){
            steps{
                sh "mvn clean package -Dmaven.test.failure.ignore=true"
            }
            post {
                success{
                    archiveArtifacts artifacts: "target/*.war", followSymlinks: false
                }
            }
        }
    }
}
