pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'my-app' // שם התמונה שתיבנה
        DOCKER_TAG = 'latest' // תגית של התמונה
        DOCKER_REGISTRY = 'docker.io' // רשם Docker
        CONTAINER_NAME = 'my-app-container' // שם הקונטיינר
    }

    stages {
        stage('Install Docker') {
            steps {
                script {
                    echo 'Installing Docker...'
                    sh '''
                    echo "jenkins" | sudo -S apt-get update
                    echo "jenkins" | sudo -S apt-get install -y apt-transport-https ca-certificates curl software-properties-common
                    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo -S apt-key add -
                    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
                    echo "jenkins" | sudo -S apt-get update
                    echo "jenkins" | sudo -S apt-get install -y docker-ce
                    sudo systemctl enable --now docker
                    '''
                }
            }
        }
    }
}
