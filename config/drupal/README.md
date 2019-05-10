This directory contains all the configuration of the site :
- .yml files
- settings files

For Drupal 8, the `sync` directory containing the site configuration files is now located in the` config / drupal` folder.
The configuration folder is located outside the files served by the web server. The path to the configuration folder is shown in settings.php.


## Creating the settings.local.php file from the install.sh script

The settings.local.php file contains the database information, the domain name and the hash salt. This file will be generated by the install.sh script from the example.settings.local.php file.

see the [launch of the starterkit](../../scripts/drupal/README.md).

[Return to project summary](../../README.md)

## Manual creation of settings.local.php
1. Copy the example.settings.local.php file
2. Name the copy settings.local.php
3. Adapt the file to your local configuration.

````php
/**
 * System configurations.
 */
// If you run the build script before creating your local settings file,
// the script will generate an example hash salt for you.
$settings['hash_salt'] = '***GENERATE SALT***';
$settings['trusted_host_patterns'] = array(
  '^***PRIOB***\.***LOC***$',
);
$databases['default']['default'] = array (
  'database' => '***DATABASE***',
  'username' => '***USERNAME***',
  'password' => '***PASSWORD***',
  'prefix' => '',
  'host' => 'mysql',
  'port' => '3306',
  'namespace' => 'Drupal\\Core\\Database\\Driver\\mysql',
  'driver' => 'mysql',
);
$config_directories['sync'] = $app_ground . '/config/drupal/sync';
$config_directories['local'] = $app_ground . '/config/drupal/local';
/**
 * Files configurations.
 */
$settings['file_public_base_url'] = 'http://***DOMAIN***/files';
$settings['file_public_path'] = $app_ground . '/web/sites/default/files';
$settings['file_private_path'] = $app_ground . '/data/files/private';
````
The settings.travis.php file will be used for testing

[Return to project summary](../../README.md)