# clue/phar-composer [![Build Status](https://travis-ci.org/clue/phar-composer.png?branch=master)](https://travis-ci.org/clue/phar-composer)

Simple phar creation for any project managed via composer.

It takes your existing project's `composer.json` and builds an executable phar
for your project among with its bundled dependencies.

* Create a single executable phar archive, including its dependencies (i.e. vendor directory included)
* Automated build process
* Zero additional configuration 

> Note: This project is in beta stage! It's been tested against a wide range
of packages and we have yet to find any major issues.
Feel free to report any issues you encounter.

## Usage

Once clue/phar-composer is [installed](#install), you can simply invoke it via command line like this:

```bash
$ phar-composer build ~/path/to/your/project
```

The second argument can be pretty much everything that can be resolved to a valid project managed by composer.
Besides creating phar archives for locally installed packages like above, you can also easily download and
bundle packages from packagist.org like this:

```bash
$ phar-composer build d11wtq/boris
```

The above will download and install the latest stable tagged release (if any).
You can also specify a tagged version like this:

```bash
$ phar-composer build clue/phar-composer:0.1.*
```

Or you can specify to install the head of a given branch like this:

```bash
$ phar-composer build clue/phar-composer:dev-master
```

A similar syntax can be used to clone a package from any git URL. This is particularly
useful for private packages or temporary git clones not otherwise listed on packagist:

```bash
$ phar-composer build https://github.com/composer/composer.git
```

The above will clone the repository and check out the default branch.
Again, you can specify either a tag or branch name very similar to how composer works:

```bash
$ phar-composer build https://github.com/composer/composer.git:dev-master
```

> As an example, this projet itself is bundled via phar-composer
([google recursion](https://www.google.com/search?q=recursion)). So instead of downloading the
below mentioned `phar-composer.phar`, you can build one yourself by issuing:
>
> ```bash
> $ php phar-composer.phar build ~/workspace/phar-composer
> ```

## Install

You can grab a copy of clue/phar-composer in either of the following ways.

### As a phar (recommended)

You can simply download a pre-compiled and ready-to-use version as a Phar
to any directory:

```bash
$ wget http://www.lueck.tv/phar-composer/phar-composer.phar
```


> If you prefer a global (system-wide) installation without having to type the `.phar` extension
each time, you may simply invoke:
> 
> ```bash
> $ chmod 0755 phar-composer.phar
> $ sudo mv phar-composer.phar /usr/local/bin/phar-composer`
> ```
>
> You can verify everything works by running:
> 
> ```bash
> $ phar-composer --version
> ```

#### Updating phar

There's no separate `update` procedure, simply overwrite the existing phar with the new version downloaded.

### Manual Installation from Source

This project requires PHP 5.3+ and Composer:

```bash
$ git clone https://github.com/clue/phar-composer.git
$ cd phar-composer
$ curl -s https://getcomposer.org/installer | php
$ php composer.phar install
```

> As an example, you can now build the above mentioned `phar-composer.phar` yourself by issuing:
>
> ```bash
> $ php bin/phar-composer build
> ```

#### Updating manually
```bash
$ git pull
$ php composer.phar update
```

## License

MIT

