node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }
    
    stage('Fetch') {
        checkout scm
    }
    
    stage('Build'){
        sh 'composer install --prefer-dist --no-dev --ignore-platform-reqs'
    }
    
    stage('config') {
        parallel(
            'config echo1': {
                echo '1'
            },
            'config echo2': {
                echo '2'
            },
            'config echo3': {
                echo '3'
            },
            'config echo4': {
                echo '4'
            },
            'config echo5': {
                echo '5'
            }
        )
    }
    
    stage('Docker Build') {
        sh 'docker build -t fabiopotame/todoapi:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'docker push fabiopotame/todoapi:$BUILD_NUMBER'
    }
}
