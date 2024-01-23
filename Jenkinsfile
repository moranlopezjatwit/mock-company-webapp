pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // TODO: Build the project using Gradle
                sh './gradlew assemble'
            }
        }

        stage('Test') {
            steps {
                // TODO: Run tests using Gradle
                sh './gradlew test'
            }
        }

        // Example stage to intentionally break the tests
        stage('Break Tests') {
            steps {
                script {
                    writeFile file: 'src/main/java/com/mockcompany/webapp/service/SearchService.java', text: '''
                        import java.util.Collections;
                        import org.springframework.stereotype.Service;
                        
                        @Service
                        public class SearchService {
                            public Collection<ProductItem> searchProducts(String query) {
                                return Collections.emptyList();
                            }
                        }
                    '''
                }
            }
        }
    }

    post {
        failure {
            echo 'Continuous Integration build has failed!'
        }
    }
}

   */
}
