# How to run processes on linux

## Run processes in background

To run process in background simply append `&` at the end of the command

    $ php artisan queue:work &

However this will terminate the background process when the terminal is exited.

To run process in background and prevent from terminating even after terminal is exited simply execute `disown` after running the process in background.

     $ php artisan queue:work &
     $ disown

## Run processes persistently in background

Running processes persistenly would make the background process run every time the machine is restarted,and power on/off.

You should use linux [supervisor](http://supervisord.org/index.html)

## Installation

Installation is simple and on Ubuntu I can install it with following command:

For Debian / Ubuntu based distro

    apt-get install supervisor

For CentOs / Fedora / RHL based distro

    sudo yum install supervisor

Supervisor configuration files are located in /etc/supervisor/conf.d directory.

    [program:email-queue]
    process_name=%(program_name)s_%(process_num)02d
    command=php /var/www/laravel-example/artisan queue:work redis --queue=emailqueue --sleep=3 --tries=3
    autostart=true
    autorestart=true
    user=forge
    numprocs=2
    redirect_stderr=true
    stdout_logfile=/var/www/laravel-example//storage/logs/supervisord.log

For each process you should create a new process configuration file. With this configuration, listener will retry each job 3 times. Also Supervisor will restart listener if it fails or if system restarts.
