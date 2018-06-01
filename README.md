# Automatically rerun PHPUnit tests when source code changes

## Usage

All the examples assume you've installed the package globally. If you opted for the local installation prepend `vendor/bin/` everywhere where `phpunit-watcher` is mentioned.

You can start the watcher with:

```bash
phpunit-watcher watch
```

This will run the tests and rerun them whenever a file in the `src` or `tests` directory is modified.

Want to pass some arguments to PHPUnit? No problem, just tack them on:

```bash
phpunit-watcher watch --filter=it_can_run_a_single_test
```

## Customization

Certain aspects of the behaviour of the tool can be modified. All options can be set in a `.phpunit-watcher.yml` in your project directory.

If a such a config file does not exist in the project directory, the tool will check if the file exists in any of the parent directories of the project directory.

Here's some example content. Read on for a more detailed explanation of all the options.

```yaml
watch:
  directories:
    - src
    - tests
  fileMask: '*.php'
notifications:
  passingTests: false
  failingTests: false
phpunit:
  arguments: '--stop-on-failure'
```

### Customize watched directories and files

You can customize the directories being watched by creating a file named `.phpunit-watcher.yml` in your project directory. Here's some example content:

```yaml
watch:
  directories:
    - src
    - tests
  fileMask: '*.php'
```

### Desktop notifications

By default the tool will display desktop notifications whenever the tests pass or fail. If you want to disable certain desktop notifications update `.phpunit-watcher.yml` by adding a `notifications` key.

```yaml
notifications:
  passingTests: false
  failingTests: false
```

### Initial PHPUnit arguments

If you want to use pass the same arguments to PHPUnit everytime to watcher starts, you can specificy those in the `.phpunit-watcher.yml` config file. Here's an example:

```yaml
phpunit:
  arguments: '--stop-on-failure'
```

When starting the tool with some arguments (eg `phpunit-watcher watch --filter=my_favourite_test`) those arguments will get used instead of the ones specified in the config file.

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Postcardware

You're free to use this package (it's [MIT-licensed](LICENSE.md)), but if you use it often we highly appreciate you sending us a postcard from your hometown, mentioning which of our package(s) you are using.

Our address is: Spatie, Samberstraat 69D, 2060 Antwerp, Belgium.

We publish all received postcards [on our company website](https://spatie.be/en/opensource/postcards).

## Credits

- [Freek Van der Herten](https://github.com/freekmurze)
- [All Contributors](../../contributors)

We started creating this package after reading [this excellent article](https://www.sitepoint.com/write-javascript-style-test-watchers-php/) by [Christoper Pitt](https://twitter.com/assertchris)

Interactive commands were inspired by [Jest](https://facebook.github.io/jest/)
