# Bitcoin Address Validator

[![Author](http://img.shields.io/badge/follow-@kielabokkie-blue.svg?logo=twitter&style=flat-square)](https://twitter.com/kielabokkie)
[![Build](https://img.shields.io/github/workflow/status/kielabokkie/bitcoin-address-validator/tests/master?style=flat-square)](https://github.com/kielabokkie/bitcoin-address-validator/actions)
[![Packagist Version](https://img.shields.io/packagist/v/kielabokkie/bitcoin-address-validator.svg?style=flat-square)](https://packagist.org/packages/kielabokkie/bitcoin-address-validator)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Total Downloads](https://img.shields.io/packagist/dt/kielabokkie/bitcoin-address-validator.svg?style=flat-square)](https://packagist.org/packages/kielabokkie/bitcoin-address-validator)

Validate legacy, segwit and native segwit (bech32) Bitcoin addresses.

## Requirements

* PHP >= 7.1

## Installation

Install the package via composer:

```
composer require kielabokkie/bitcoin-address-validator
```

## Usage

First you instantiate the the validator class:

```php
$addressValidator = new \Kielabokkie\Bitcoin\AddressValidator;
```

Validate any kind of address (legacy, segwit and native segwit):

```php
$addressValidator->isValid('1AGNa15ZQXAZUgFiqJ2i7Z2DPU2J6hW62i');
```

Legacy (P2PKH) address:

```php
$addressValidator->isPayToPublicKeyHash('1AGNa15ZQXAZUgFiqJ2i7Z2DPU2J6hW62i');
```

Segwit (P2SH) address:

```php
$addressValidator->isPayToScriptHash('3ALJH9Y951VCGcVZYAdpA3KchoP9McEj1G');
```

Native segwit (bech32) address:

```php
$addressValidator->isBech32('bc1qw508d6qejxtdg4y5r3zarvary0c5xw7kv8f3t4');
```

### Testnet

By default the validator only passes mainnet addresses as valid. If you would like to validate both mainnet and testnet addresses you can use method chaining:

```php
// Both valid
$addressValidator->includeTestnet()->isBech32('bc1qw508d6qejxtdg4y5r3zarvary0c5xw7kv8f3t4');
$addressValidator->includeTestnet()->isBech32('tb1qw508d6qejxtdg4y5r3zarvary0c5xw7kxpjzsx');
```

If you want to validate only testnet addresses you can do that as follows:

```php
// Invalid
$addressValidator->onlyTestnet()->isBech32('bc1qw508d6qejxtdg4y5r3zarvary0c5xw7kv8f3t4');
// Valid
$addressValidator->onlyTestnet()->isBech32('tb1qw508d6qejxtdg4y5r3zarvary0c5xw7kxpjzsx');
```

## Testing

This package is tested against the test data of the official [bitcoin/bitcoin](https://github.com/bitcoin/bitcoin/tree/master/src/test/data) repo. If you come across an address that is not validated correctly please [open an issue](https://github.com/kielabokkie/bitcoin-address-validator/issues) for it.

Run the tests with:

```bash
composer test
```

## Credits

This package is based on the following packages and uses a lot of their code:

* [bitwasp/bech32](https://github.com/Bit-Wasp/bech32) by [@afk11](https://github.com/afk11)
* [linusu/bitcoin-address-validator](https://github.com/LinusU/php-bitcoin-address-validator) by [@LinusU](https://github.com/LinusU)

All credit goes to the original authors.

## Donate

Did this package save you some time or spark joy?

A donation would be much appreciated: `32vtWJSomccxQ6y1tgSwSHXN5PChpdYy27`
