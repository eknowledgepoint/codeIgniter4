node {
    stage("composer_install") {
        php 'composer install'
    }

    stage("php_lint") {
        php 'find . -name "*.php" -print0 | xargs -0 -n1 php -l'
    }

    stage("phpunit") {
        php 'vendor/bin/phpunit'
    }

    stage("codeception") {
        php 'vendor/bin/codecept run'
    }
	
	stage("clone") {
        sh 'git clone https://github.com/eknowledgepoint/codeIgniter4.git'
    }
	
	
	stage("publish") {
       sh 'sudo cp -r /var/lib/jenkins/workspace/codeigniter4/codeIgniter4/ /var/www/html/'
	   sh 'rm -r /var/lib/jenkins/workspace/codeigniter4/codeIgniter4'
    }
}