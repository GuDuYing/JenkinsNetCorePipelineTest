#!/测试

pipeline {
    agent any
    stages {
        stage('build-test') {
            steps {
                sh 'dotnet restore ./WebApiTest.sln'
                sh 'dotnet build ./WebApiTest.sln'
                sh 'dotnet test --no-build --no-restore ./WebApiTest.Data.Tests/'
            }
        }

        
    }
}