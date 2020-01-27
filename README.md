# composer-setup-for-code-sniffer

## Do the following steps in order:

1. copy git-hooks/pre-commit from this repository to the root directory of your git repository


2. Inside composer.json file, add a new event to `post-install-cmd` inside `scripts` like as under

    "scripts": {
        "post-install-cmd": [
            "@php -r \"copy('git-hooks/pre-commit', '.git/hooks/pre-commit') && (file_exists('phpcs.xml') || copy('phpcs.xml.example', 'phpcs.xml'));\""
        ]
    }
    
3. Installation: Run following commands in order:
    `composer require --dev squizlabs/php_codesniffer`
    `composer run-script post-install-cmd` 
