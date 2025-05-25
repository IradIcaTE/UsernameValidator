pipeline {

    agent { label "First" }
    
    environment {
        USERS = "alice,bob,charlie"
        BLOCKED = "bob"
    }

    parameters {
        string( name: "USERNAME", defaultValue: "alice", description: "Enter a user to validate" )
    }

    stages {

        stage("Check Username") {
            steps {
                script {
                    def userList = env.USERS.split(',')
                    def blockedList = env.BLOCKED.split(',')

                    if (!userList.contains(param.USERNAME)) {
                        echo "User '${params.USERNAME} is not in the allowed list"
                    }

                    if (blockedList.contains(params.USERNAME)) {
                        echo "User '${params.USERNAME} is BLOCKED!"
                    }

                    echo "User '${params.USERNAME} is allowed and not blocked'"
                }
            }
        }
    }
}