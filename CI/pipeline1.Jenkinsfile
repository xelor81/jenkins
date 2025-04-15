pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Ansible') {
            when {
                expression {
                    return params.ANSIBLE_RUN ==~ /(?i)(Y|YES|T|TRUE|ON|RUN)/
                }
            }
            steps {
                ansiblePlaybook
                    credentialsId: 'ansible',
                    installation: 'ansible2.14',
                    inventory: '/projects/devops/ansible/inventory/local.lab/local.lab_hosts.yml',
                    playbook: '/projects/devops/ansible/playbooks/ecom/hosts_fix.yml',
                    extraVars: [
                        parameter: "${PARAM1}",
                        parameter2: "${PARAM2}"
                        ],
                    vaultTmpPath: ''
            }
        }
        stage('Trigger job2'){
            steps {
                echo 'Call job2 ==========================================='
                build job: 'job2',
                    wait: true
            }
        }
    }
}
