# WordPress Docker Environment
Basic template for working on WordPress within Docker, on remote Linux hosts, with VSCode.  
By default it comes with a PhpMyAdmin instance, so you don't have to install any SQL client.  

## Setup
1. Connect to your Linux development server, with Docker installed, via SSH in VSCode and `git clone` this repo. Additional steps may be needed when working with other environments.
2. Copy `.env.example` to `.env` and modify as needed.
3. Copy `./wordpress/example-php.ini` to `./wordpress/php.ini` and modify as needed.
4. Copy `./wordpress/conf.d/example-error_reporting.ini` to `/wordpress/conf.d/error_reporting.ini` and modify as needed.
5. Copy `./wordpress/conf.d/example-xdebug.ini` to `./wordpress/conf.d/xdebug.ini` and modify as needed.
6. Run `docker compose build && docker compose up -d`
7. Run `sudo chown -R [your local user] ./wordpress/data` to gain ownership of WordPress files you want to work on. This only makes it easier for you to directly save from VSCode.
8. Click the VSCode debug button from this directory. Create a launch.json to Listen for Xdebug. Your launch.json must have the correct path mapping like so...
```json
"configurations": [
{
    "name": "Listen for Xdebug",
    "type": "php",
    "request": "launch",
    "port": 9003,
    "pathMappings": {
        "/var/www/html": "${workspaceFolder}/wordpress/data",
    }
},
]
```

## WordPress Development
### Step Debugging
After following the above steps, step debugger should work 'out-of-box'. Click the debug button in VSCode and listen for XDebug. You can test this by adding a stop point in index.php.  

### XDebug Logs
The default location for these is found in the /tmp directory of the WordPress container. You can define it otherwise in the php.ini file. Mapping it to a volume would be a good idea if you frequently check this log. Check here if you are having issues with XDebug working.
