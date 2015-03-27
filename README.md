![Build Status](http://ec2-52-10-26-150.us-west-2.compute.amazonaws.com/build-status/image/3)

#PHPCI

##Drupal plugin

Drupal plugin for PHPCI that allows building a Drupal installation profile and execute drush test commands.

### Configuration

#### Dependency

* MySQL plugin

#### Build Settings

Drupal settings.

```
	drupal:
		sitename: '[name of the site]'
		dbhost: '[database host e.g. 127.0.0.1]'
		dbport: '[database port e.g. 3306]'
		dbuser: '[database username]'
		dbpass: '[databse password]'
		dbname: '[database name]'
		accountname: ‘[Drupal account name]’
		accountpass: ‘[Drupal account password]'
		profile: ‘[Drupal profile]'
		mail: ‘[admin e-mail address. e.g.]’
```

#### Setup

Drush commands to run before tests.

```
setup:
	drupal:
			- “drush -y pm-enable behatrunner”
```

#### Test

Test command(s) to run.

```
test:
	drush:
		features: brun
```

### Example

```
build_settings:
    mysql:
        host: 'localhost'
        user: 'drupal'
        pass: '12345678'
    drupal:
        sitename: 'Lightning'
        dbhost: '127.0.0.1'
        dbport: '3306'
        dbuser: 'drupal'
        dbpass: '12345678'
        dbname: 'lightning'
        profile: 'standard'
        mail: 'wouter.adem@gmail.com'

setup:
    mysql:
        - "CREATE DATABASE lightning;"
    drupal:
        - "drush -y pm-enable behatrunner"

test:
  drush:
    features: brun

complete:
    mysql:
        - "DROP DATABASE lightning;"
```