pipeline {

	agent any

	tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    environment {

        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'admin'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-mven-central'
        NEXUSIP = '172.31.60.58'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
        }

    stages{


        stage('BUILD'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }

            post{
            success {
            echo "Now archiving"
            archiveArtifacts artifacts: '**/*.war'
            }}

            stage('Test'){
            steps{
            sh 'mvn test'}
            }

            stage('Checkstyle analysis'){
                        steps{
                        sh 'mvn checkstyle: checkstyle'}
                        }


        }

        }



}
