PHPCompability - EasyWay
========================

## About
Whenever we need to upgrade the PHP version we need to worry about discontinued methods and other peculiarities. Using the standard PHPCompability we can check what impacts our application will have if we make this migration, facilitating problem solving and validation of the source code.

## Install

Execute the command below to get the dependencies.
```
    composer update
```


Make sure your project have the dependencies below.

#### composer.json
```
{
    "require": {
        "squizlabs/php_codesniffer": "^2.7",
        "wimg/php-compatibility": "^7.0",
        "simplyadmire/composer-plugins": "^2.1"
    }
}
```

After that you will need to move the "php-compability" folder into the "./vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/" folder. To do this, run the following command:

```
    mv /var/www/project/testes/PHPCompability/vendor/wimg/php-compatibility /var/www/project/testes/PHPCompability/vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/PHPCompatibility
```

## Running tests

I have created a list of commands to facilitate learning and demonstrate various possibilities for displaying and handling errors. Note below:

* Displays which defaults are installed
```
./vendor/bin/phpcs -i
```

* Shows available commands
```
./vendor/bin/phpcs -h
```

* Running with version 5.3
```
./vendor/bin/phpcs --standard=PHPCompatibility --runtime-set testVersion 5.3 /var/www/project/testes/PHPCompability/
```

* Running with version 7 and just with "php" extension
```
./vendor/bin/phpcs --standard=PHPCompatibility --extensions=php --runtime-set testVersion 7 /var/www/project/testes/PHPCompability/
```

* Running with version 7, just with "php" extension and ignoring the folders 'tests' and 'vendor'.
```
./vendor/bin/phpcs --standard=PHPCompatibility --extensions=php --runtime-set testVersion 7 --ignore=*/tests/*,*/vendor/* /var/www/project/testes/PHPCompability/
```

* Running with version 7, just with "php" extension, ignoring the folders 'tests' and 'vendor' and exporting to text file.
```
./vendor/bin/phpcs --standard=PHPCompatibility --extensions=php --runtime-set testVersion 5.3 --ignore=*/tests/*,*/vendor/* /var/www/project/testes/PHPCompability/ > teste.txt
```

* Running with version 7, just with "php" extension, ignoring the folders 'tests' and 'vendor' and ignoring "Warning".
```
./vendor/bin/phpcs --standard=PHPCompatibility --extensions=php -n --runtime-set testVersion 5.3 --ignore=*/tests/*,*/vendor/* /var/www/project/testes/PHPCompability/
```

* Running with version 7, just with "php" extension, ignoring the folders 'tests' and 'vendor, exporting to text file and ignoring "Warning".
```
./vendor/bin/phpcs --standard=PHPCompatibility --extensions=php -n --runtime-set testVersion 5.3 --ignore=*/tests/*,*/vendor/* --report-file=teste.txt /var/www/project/testes/PHPCompability/
```
 
* Running with version 7, just with "php" extension, ignoring the folders 'tests' and 'vendor' and exportando no formato HTML
	
```
./vendor/bin/phpcs --standard=PHPCompatibility --extensions=php --runtime-set testVersion 7 --ignore=*/tests/*,*/vendor/* --generator=HTML /var/www/project/testes/PHPCompability/
```


## Available Commands ( source : pear.php.net )
```
	Usage: phpcs [-nwlsapvi] [-d key[=value]]
    [--report=<report>] [--report-file=<reportfile>] [--report-<report>=<reportfile>] ...
    [--report-width=<reportWidth>] [--generator=<generator>] [--tab-width=<tabWidth>]
    [--severity=<severity>] [--error-severity=<severity>] [--warning-severity=<severity>]
    [--config-set key value] [--config-delete key] [--config-show]
    [--standard=<standard>] [--sniffs=<sniffs>] [--encoding=<encoding>]
    [--extensions=<extensions>] [--ignore=<patterns>] <file> ...
        -n            Do not print warnings (shortcut for --warning-severity=0)
        -w            Print both warnings and errors (on by default)
        -l            Local directory only, no recursion
        -s            Show sniff codes in all reports
        -a            Run interactively
        -p            Show progress of the run
        -v[v][v]      Print verbose output
        -i            Show a list of installed coding standards
        -d            Set the [key] php.ini value to [value] or [true] if value is omitted
        --help        Print this help message
        --version     Print version information
        <file>        One or more files and/or directories to check
        <extensions>  A comma separated list of file extensions to check
                      (only valid if checking a directory)
        <patterns>    A comma separated list of patterns to ignore files and directories
        <encoding>    The encoding of the files being checked (default is iso-8859-1)
        <sniffs>      A comma separated list of sniff codes to limit the check to
                      (all sniffs must be part of the specified standard)
        <severity>    The minimum severity required to display an error or warning
        <standard>    The name or path of the coding standard to use
        <tabWidth>    The number of spaces each tab represents
        <generator>   The name of a doc generator to use
                      (forces doc generation instead of checking)
        <report>      Print either the "full", "xml", "checkstyle", "csv", "emacs"
                      "source", "summary", "svnblame" or "gitblame" report
                      (the "full" report is printed by default)
        <reportfile>  Write the report to the specified file path
        <reportWidth> How many columns wide screen reports should be printed
```

#### References:
 
* pear.php.net
* https://www.sitepoint.com/quick-intro-phpcompatibility-standard-for-phpcs-are-you-php7-ready/