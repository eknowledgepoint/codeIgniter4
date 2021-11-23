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
	
	stage("publish") {
        sh 'cd /var/www/html/'
		sh 'git pull origin master'
    }
}