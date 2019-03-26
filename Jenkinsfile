node('mavenbuilds'){
    def mvnHome = tool name: 'maven360', type: 'maven'
    stage('checkout'){
        echo "downloading the source code"
      // git credentialsId: 'git_token', url: 'https://github.com/amritlamsal123/simple-java-maven-app.git'
        echo "successfully checkout"
    }
    stage('execute test case'){
        echo "executing test cases"
        sh "${mvnHome}/bin/mvn clean test"
        archiveArtifacts allowEmptyArchive: true, artifacts: 'target/surefire-reports*.xml'
        junit allowEmptyResults: true, testResults: 'target/surefire-reports*.xml'
    }
    stage('build'){
        echo "building the job now"
        sh "${mvnHome}/bin/mvn clean package"
    }
    stage('post build'){
        echo "email to the user about the build status"
    }

}
