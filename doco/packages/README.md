# `coinpm` package types

The coin package manager aims to have several types of packages. Some of these packages will be particular to a single crypto currency, and other will be agnostic to them.

## documentation

Packages whose `type` is `documentation` are expected to provide documentation, and usually static HTML will be all that is expected.

## auth

Packages whose `type` is `auth` are expected to provide security enhancement through authentication and authorisation methods. At a basic level, it provides a means to define username and pasword combinations for various actions.

## backup

Packages whose `type` is `backup` are expected to provide one or more back up options for crypto currency wallets. The objective is to provide an easy to use wrapper around backup utilities such as truecrypt, or more interestingly a wrapper around combinations of backup utilities. Additionally backup packages may be in charge of more advanced functionality, such as providing cols storage facilities, generating QR codes and printing of paper wallets may also be included.

## wallet

The functions of generating public/ private key pairs for a particular crypto currency and sending or receiving payments is what is expected as a basic level of functionality from a package whose `type` is `wallet`. Wallet packages are expected to work closely with auth and backup modules.

## tracker

Package with the `type` of `tracker` provide means to interface with web APIs. Example usages include polling coinchoose and coinwarz, mining pool statuses, exchange rates, et cetera.

## miner

Packages with the `type` of `miner` provide the ability to mine crypto currencies. These might provide a means to mine just once crypto currency or multiple crypto currencies (multi-mining) by integrating with tracker modules. These might provide both solo mining and multi mining options. These will typically be acheived by wrapping around existing mining tools such as cpuminer, cgminer, and bfgminer.

## exchange

Packages with the `type` of `exchange` provide the ability to exchange one crypto currency with another at minimum. They might also provide the means to exchange crypto currency with fiat currency. They may integrate with online exchange account APIs, or they may use peer exchange mechanisms via protocols such as coloured coins, or both.

## strategy

Packages with the `type` of `strategy` are intended to be ways in which users prefer to combine their use of the other packages. A user may author their own strategy, or reuse poular ones that serve as "recipes". Strategies for miners, traders, and holders will be different. These should provide a means for the user to declaratively specify actions to be performed. For example, a miner might describe their stratgey as "poll coinwarz every 30 minutes, and mine the top 3 most profitable coins, and these are the pools that we should use".
