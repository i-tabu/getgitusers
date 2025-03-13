<p align="center"> 
  <img src="https://github.com/user-attachments/assets/53db248e-6429-4a04-b063-5e8d1f60cd61" alt="Download Git Users">
</p>

ABOUT
============
Very quick script, to seach github users according to their language, location and download inside a MySQL table.

INSTALLATION
============
***Download the code***
```
mkdir getgitusers
cd getgitusers
git clone https://github.com/itabrezshaikh/getgitusers.git .
```

**Download Composer**
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'.PHP_EOL; } else { echo 'Installer corrupt'.PHP_EOL; unlink('composer-setup.php'); exit(1); }"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

***Install dependencies***
```
php composer.phar install
```

***Create database and table***
```
create database github;
use github;
```
```
CREATE TABLE `users` (
 `id` int(11) DEFAULT NULL,
 `login` varchar(255) DEFAULT NULL,
 `url` varchar(255) DEFAULT NULL,
 `site_admin` tinyint(1) DEFAULT NULL,
 `name` varchar(255) DEFAULT NULL,
 `company` varchar(255) DEFAULT NULL,
 `blog` varchar(255) DEFAULT NULL,
 `location` varchar(255) DEFAULT NULL,
 `email` varchar(255) DEFAULT NULL,
 `hireable` tinyint(1) DEFAULT NULL,
 `bio` varchar(255) DEFAULT NULL,
 `public_repos` int(11) DEFAULT NULL,
 `public_gists` int(11) DEFAULT NULL,
 `followers` int(11) DEFAULT NULL,
 `following` int(11) DEFAULT NULL,
 `created_at` datetime DEFAULT NULL,
 `updated_at` datetime DEFAULT NULL,
 `score` INT,
 PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```
***Edit src/GetGitUsers.php - modify the database connection & search params***

***GetGitUsers.php***
```php
...
//modify these params-------------
$this->test_mode = 0;
$this->db = new MysqliDb ('yourlocalhost', 'yourdbuser', 'yourdbpass', 'yourdbname');
$language = 'php';
$location = 'mumbai';
$sort = 'followers';
//--------------------------------
...
```

USAGE
=====
```
php run.php
```

