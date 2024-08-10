Sample Jenkins pipelines
------------------------

# Dev Pipeline
```
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git '(link unavailable)'
                sh 'mvn clean package'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-app .'
            }
        }
        stage('Push to JFrog') {
            steps {
                sh 'docker tag my-app <JFROG_URL>/my-app:latest'
                sh 'docker push <JFROG_URL>/my-app:latest'
            }
        }
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve -var-file=dev.tfvars'
            }
        }
        stage('Deploy to Dev') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
        stage('Selenium Tests (Smoke)') {
            steps {
                sh 'mvn selenium:selenium'
            }
        }
    }
    post {
        always {
            sh 'echo "Pipeline completed"'
        }
    }
}
```

# QA Pipeline

```
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git '(link unavailable)'
                sh 'mvn clean package'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-app .'
            }
        }
        stage('Push to JFrog') {
            steps {
                sh 'docker tag my-app <JFROG_URL>/my-app:latest'
                sh 'docker push <JFROG_URL>/my-app:latest'
            }
        }
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve -var-file=qa.tfvars'
            }
        }
        stage('Deploy to QA') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
        stage('Selenium Tests (Full Regression)') {
            steps {
                sh 'mvn selenium:selenium'
            }
        }
        stage('Performance Tests') {
            steps {
                sh 'jmeter -n -t performance.jmx'
            }
        }
    }
    post {
        always {
            sh 'echo "Pipeline completed"'
        }
    }
}
```

# Prod Pipeline

```
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git '(link unavailable)'
                sh 'mvn clean package'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve -var-file=prod.tfvars'
            }
        }
        stage('Deploy to Prod') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
        stage('Selenium Tests (Smoke)') {
            steps {
                sh 'mvn selenium:selenium'
            }
        }
    }
    post {
        always {
            sh 'echo "Pipeline completed"'
        }
    }
}
```