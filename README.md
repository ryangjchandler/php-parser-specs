# PHP Parser Specs

This repository contains a set of PHP files that can be used to test the compliance of a PHP parser.

All of the tests are designed to prove correctness. There are no tests to check that the parser correctly handles erroneous code, since some parsers are error tolerant and others will use different error messages to PHP itself.

Each test contains a code snippet containing valid PHP code. In the future, I'd like to also add a simple representation of the parsed code so that parsers can convert their own AST into the same format and test against that, instead of relying on status codes.

A test runner can be found at `/bin/run-parser-specs`.

The test runner accepts a single argument &mdash; the name of a binary, or command, that you wish to send the test file through.

```sh
./bin/run-parser-specs "./parse"
```

By default, the file will be appended to the given command and executed. The return code of the command is used to determine success. If a non-zero return code is detected, the output will be captured and output in the terminal.

If you are passing a command and would like to change where or how the file name is passed through, you can use the `<>` placeholder in the command string.

```sh
./bin/run-parser-specs "./program --only-parse=<>"
```

This will execute the command `./program --only-parse=path/to/spec/file.php`.

## Baseline

To ensure that all of the spec files are in accordance with PHP itself, all spec files are tested with PHP using the `php -l` command.

## Contributing

All contributions are welcome.

Ensure pull requests contain a brief description about the changes made, all tests pass and code is formatted correctly.