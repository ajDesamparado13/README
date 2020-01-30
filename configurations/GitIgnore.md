# Git Ignore File Configurations

Common:

    /vendor
    /node_modules
    /public/hot
    /public/storage
    /public/_.js
    /public/js
    /public/_.css
    /public/mix-manifest.json
    /public/css
    /public/.htaccess
    /public/fonts/\*
    /.idea
    /.vscode
    /.vagrant
    .env
    .phpunit.result.cache
    Homestead.json
    Homestead.yaml
    npm-debug.log
    yarn-error.log
    tags
    tags.lock
    tags.temp
    /storage/debugbar

Must be deliberated:

    package-lock.json
    composer.lock

Depending on how the deliverables is being released, the lock files may or may not be needed to be tracked into the version control.
