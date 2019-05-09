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
    stage('Publish') {
            steps{
              bat  '''
               dotnet build ./WebApiTest/WebApiTest.csproj'
               dotnet publish ./WebApiTest/WebApiTest.csproj -o "$(pwd)/publish" --framework netcoreapp2.2
               '''
               echo 'Core Delivery Service Build & Publish Done'
            }
        }
        
    }
}