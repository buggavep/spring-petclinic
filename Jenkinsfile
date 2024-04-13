pipeline {
    agent {
        docker {
            image 'buggavep/sample-devops:9.0'
            args '-v /var/run/docker.sock:/var/run/docker.sock -u root'
        }
    }
    
    stages {
        stage('Compile') {
            steps {
                sh '''
                    #!/usr/bin/bash
                    ./mvnw clean package
                '''
            }
        }
        stage('Build Image') {
            steps {
                sh '''
                    #!/usr/bin/bash
                    ./mvnw spring-boot:build-image -Dspring-boot.build-image.imageName=buggavep/spring-petclinic:1.0
                    docker image list
                '''
            }
        }
        
        // stage('Push') {
        //     steps {
        //         withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
        //             sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
        //             sh 'docker tag docker.io/library/spring-petclinic:3.2.0-SNAPSHOT buggavep/spring-petclinic:1.0'
        //             sh 'docker push buggavep/spring-petclinic:1.0'
        //         }
        //     }
        // }
    }
}