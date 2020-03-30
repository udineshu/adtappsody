pipeline {
    agent any

 environment {
                OC_TOKEN   = "jenkinsToken"
                OC_PROJECT = "order"
                OC_URL = "https://okd.wiprodx.com:8443/"
                OC_NAMESPACE = "dmp"
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building....'
                 sh '/opt/maven/bin/mvn clean install -Dmaven.test.skip=true'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                 sh 'oc login -u admin -p admin https://okd.wiprodx.com:8443 --insecure-skip-tls-verify'
                 sh 'oc project $OC_NAMESPACE'
                 sh 'oc delete all -l app=$OC_PROJECT --ignore-not-found=true --grace-period=0 --force=true'
                 sh 'oc new-app talk2me19/$OC_PROJECT'
                 sh 'oc expose svc/$OC_PROJECT'
            }
        }
    }
}
