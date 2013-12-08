# `coinpm` package types

The coin package manager aims to have several types of packages. Some of these packages will be particular to a single crypto currency, and other will be agnostic to them.

## documentation

Packages whose `type` is `documentation` are expected to provide documentation, and usually static HTML will be all that is expected.

	{
		"name": "foodocument",
		"type": "documentation",
		"description": "a package that documents foo",
		"source": "https://github.com/bguiz/coinpm-foodocument",
		"version": "0.0.0",
		"commands": {
			"run": "coinpm browser index.html"
		},
		"dependencies": [],
		"author": {
			"moniker": "bguiz",
			"addresses": {
				"BTC": "1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG"
			}
		}
	}

## auth

Packages whose `type` is `auth` are expected to provide security enhancement through authentication and authorisation methods. At a basic level, it provides a means to define username and pasword combinations for various actions.

	{
		"name": "fooauth",
		"type": "auth",
		"description": "a package that documents foo",
		"source": "https://github.com/bguiz/coinpm-fooauth",
		"version": "0.0.0",
		"commands": {
			"run": "fooauth.sh"
		},
		"dependencies": [],
		"author": {
			"moniker": "bguiz",
			"addresses": {
				"BTC": "1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG"
			}
		}
	}

## backup

Packages whose `type` is `backup` are expected to provide one or more back up options for crypto currency wallets. The objective is to provide an easy to use wrapper around backup utilities such as truecrypt, or more interestingly a wrapper around combinations of backup utilities. Additionally backup packages may be in charge of more advanced functionality, such as providing cols storage facilities, generating QR codes and printing of paper wallets may also be included.

	{
		"name": "foocoinbarcoinbackup",
		"type": "backup",
		"description": "back up utility for foocoin and barcoin",
		"source": "https://github.com/bguiz/coinpm-foocoinbarcoinbackup",
		"version": "0.0.0",
		"commands": {
			"run": "walletbackup.sh start-gui",
			"doco": "coinpm run coinpm_modules/foocoinbarcoinbackupdocument",
			"*": "walletbackup.sh #{*}"
		},
		"dependencies": [
			"foocoinbarcoinbackupdocument": "0.0.0",
			"truecrypt": "7.1a"
		],
		"optionalDependencies": [
			"foocoinwallet": "0.0.0",
			"barcoinwallet": "0.0.0"
		],
		"author": {
			"moniker": "bguiz",
			"addresses": {
				"BTC": "1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG"
			}
		}
	}

## wallet

The functions of generating public/ private key pairs for a particular crypto currency and sending or receiving payments is what is expected as a basic level of functionality from a package whose `type` is `wallet`. Wallet packages are expected to work closely with auth and backup modules.

	{
		"name": "foocoinwallet",
		"type": "wallet",
		"description": "a wallet for foo coins",
		"source": "https://github.com/bguiz/coinpm-foowallet",
		"version": "0.0.0",
		"commands": {
			"run": "foocoinwallet.sh start-gui",
			"doco": "coinpm run coinpm_modules/foodocument",
			"*": "foocoinwallet.sh #{*}"
		},
		"dependencies": [
			"foodocument": "0.0.0",
			"qr-code-generator": "0.0.0"
		],
		"author": {
			"moniker": "bguiz",
			"addresses": {
				"BTC": "1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG"
			}
		}
	}

## tracker

Package with the `type` of `tracker` provide means to interface with web APIs. Example usages include polling coinchoose and coinwarz, mining pool statuses, exchange rates, et cetera.

	{
		"name": "footracker",
		"type": "tracker",
		"description": "a package that tracks coin prices",
		"source": "https://github.com/bguiz/coinpm-footracker",
		"version": "0.0.0",
		"commands": {
			"run": "footracker.sh --source coinchoose"
		},
		"dependencies": [
			"qryq": "0.0.9"
		],
		"author": {
			"moniker": "bguiz",
			"addresses": {
				"BTC": "1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG"
			}
		}
	}

## miner

Packages with the `type` of `miner` provide the ability to mine crypto currencies. These might provide a means to mine just once crypto currency or multiple crypto currencies (multi-mining) by integrating with tracker modules. These might provide both solo mining and multi mining options. These will typically be acheived by wrapping around existing mining tools such as cpuminer, cgminer, and bfgminer.

	{
		"name": "foominer",
		"type": "tracker",
		"description": "a package that mines foocoin",
		"source": "https://github.com/bguiz/coinpm-foocoinminer",
		"version": "0.0.0",
		"commands": {
			"run": "foominer.sh"
		},
		"dependencies": [
			"foocoinwallet": "0.0.0"
		],
		"author": {
			"moniker": "bguiz",
			"addresses": {
				"BTC": "1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG"
			}
		}
	}

## exchange

Packages with the `type` of `exchange` provide the ability to exchange one crypto currency with another at minimum. They might also provide the means to exchange crypto currency with fiat currency. They may integrate with online exchange account APIs, or they may use peer exchange mechanisms via protocols such as coloured coins, or both.

	{
		"name": "foocoinexchange",
		"type": "exchange",
		"description": "a package that trades foocoin",
		"source": "https://github.com/bguiz/coinpm-foocoinexchange",
		"version": "0.0.0",
		"commands": {
			"run": "foocoinexchange.sh --exchange all"
		},
		"dependencies": [
			"foocoinwallet": "0.0.0"
		],
		"author": {
			"moniker": "bguiz",
			"addresses": {
				"BTC": "1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG"
			}
		}
	}

## strategy

Packages with the `type` of `strategy` are intended to be ways in which users prefer to combine their use of the other packages. A user may author their own strategy, or reuse poular ones that serve as "recipes". Strategies for miners, traders, and holders will be different. These should provide a means for the user to declaratively specify actions to be performed.

	{
		"name": "foostrategy",
		"type": "exchange",
		"description": "a package for executing the foo stratgey",
		"source": "https://github.com/bguiz/coinpm-foocoinexchange",
		"version": "0.0.0",
		"commands": {
			"run": "foostrategy.sh --exchanges all"
		},
		"dependencies": [
			"foocoinexchange": "0.0.0",
			"foocoinexchange": "0.0.0",
			"foocoinwallet": "0.0.0",
			"footracker": "0.0.0"
		],
		"author": {
			"moniker": "bguiz",
			"addresses": {
				"BTC": "1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG"
			}
		},
		"config": {
			"miner-strategy": {
				"type": "most-profitable",
				"params": {
					"maxSimultaneous": "3",
					"poll-frequency": "30m",
					"tracker": {
						"name": "coinwarz",
						"api-key": "zxcvbnm1234567"
				}
			}
		}
	}

For example, the above `config` could be used by a miner who describes their strategy as "poll coinwarz every 30 minutes, and mine the top 3 most profitable coins, and these are the pools that we should use".

----

Like this idea enough to tip?

bitcoin:1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG
![bitcoin:1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG ](https://chart.googleapis.com/chart?cht=qr&chl=bitcoin%3A1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG&choe=UTF-8&chs=200x200)

