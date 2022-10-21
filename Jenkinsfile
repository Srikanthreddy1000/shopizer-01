pipeline {
    agent {label "java-11"}
    parameters {
        choice(name: 'git-branch', choices: ["developr", "master"], description: 'for branches')
        string(name: 'mvn-pk', defaultValue: "mvn package", description: 'build the package')
    }
    stages {
        stage('Git') {
            steps {
                git branch: "${params.git-branch}",
                url: 'https://github.com/Srikanthreddy1000/shopizer-01.git'
            }
        }
        stage('mavenbuild') {
            steps {
                sh "${params.mvn-pk}"
            }
        }
        stage('artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
            }
        }
        stage('Junits') {
            steps {
                junit '**/surefire-reports/*.xml'
            }
        }
    }
}