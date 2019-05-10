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
                sh 'dotnet build ./WebApiTest/WebApiTest.csproj'
                sh 'dotnet publish ./WebApiTest/WebApiTest.csproj -o "$(pwd)/publish" --framework netcoreapp2.2'
                echo 'publish done'
            }
        }
    stage('Deploy To Server') {
            steps{
            sshPublisher(publishers: [sshPublisherDesc(configName: 'Tencent2', 
            transfers: [sshTransfer(cleanRemote: false, excludes: '', 
            execTimeout: 120000, 
            flatten: false, 
            makeEmptyDirs: false, 
            noDefaultExcludes: false, 
            patternSeparator: '[, ]+', 
            remoteDirectory: 'WebApiTest/', 
            remoteDirectorySDF: false, 
            removePrefix: '$publish/', 
            sourceFiles: 'publish/**')], 
            usePromotionTimestamp: false, 
            useWorkspaceInPromotion: false, 
            verbose: false,
            execCommand: '''pwd''',
            )])
            echo 'Deploy To Server Done'    
            }
        }
        
    }
}