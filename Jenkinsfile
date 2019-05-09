#!/测试

pipeline {
    agent any
    stages {
        stage('build-test') {
            steps {
                sh 'dotnet restore ./WebApiTest/WebApiTest.csproj'
                sh 'dotnet build ./WebApiTest/WebApiTest.csproj'
            }
        }

        
    }
}