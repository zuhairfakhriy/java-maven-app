@Library('jenkins-shared-library') _

pipeline {
    agent any
    tools {
        maven 'maven-3.9'
    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy" 
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    gv.buildJar() 
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    gv.buildImage 'azeshion21/demo-app:jma-3.0'
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    gv.deployApp() 
                }
            }
        }
    }
}

