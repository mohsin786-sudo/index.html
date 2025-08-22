pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/your-username/your-website-repo.git'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                // If Jenkins & Nginx are on different server
                sshagent(['my-server-ssh']) {
                    sh '''
                    echo "Deploying website to server..."
                    rsync -avz --delete ./ /var/www/html/
                    sudo systemctl restart nginx
                    '''
                }

                // If Jenkins & Nginx are on SAME machine, use this instead:
                // sh '''
                // cp -r * /var/www/html/
                // sudo systemctl restart nginx
                // '''
            }
        }
    }
}
