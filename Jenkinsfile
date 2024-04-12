pipeline {
    agent {
        docker {
            image 'buggavep/sample-devops:9.0'
            args '-v /var/run/docker.sock:/var/run/docker.sock -u root'
        }
    }
    
    stages {
        stage('Build') {
            steps {
                sh './mvnw package'
            }
        }
        
        // stage('Package') {
        //     steps {
        //         sh 'docker build -f Dockerfile-8u131 -t buggavep/hello-world .'
        //     }
        // }
        
        // stage('Push') {
        //     steps {
        //         withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
        //             sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
        //             sh 'docker tag buggavep/hello-world buggavep/hello-world:latest'
        //             sh 'docker push buggavep/hello-world:latest'
        //         }
        //     }
        // }
    }
}