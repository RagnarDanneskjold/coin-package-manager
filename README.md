# Coin Package Manager

## Premise

- Many different crypto currencies
- Many different things you can do with each one
- Need to be technically minded to understand how to use them properly
- Even if one is tech savvy, keeping track of all of them can still be very time consuming
- Would it not be better if there was a standard interface to interact with each type of cryptocurrency
- ... and of course, this standard way distributed (not a central registry)

## Proposal

- Inspired by npm for nodejs, pip for python, gem for ruby
	- But "registry" is peer to peer
- Users can create their own node by serving as a project on github/ bitbucket, et cetera, and serve a reference to it on their own node
- Users can review the source for these packages, install them, run them, and rate them
- Users can publish their own packages

### Sample workflow

	#start your own private package as a means to use others
	coinpm init --private=true mycoins

	#modify any configurations
	$EDITOR ./package.json
	cd ./mycoins

	#open browser at repository page
	coinpm review foopackage

	#install a package as a dependency, and add to your private package configuration
	coinpm install --save foopackage

	#run your private package, including the package just installed as a dependency
	coinpm run

	#rate the package installed 100% on your node
	coinpm rate foopackage 100

## Types of packages

What sort of packages will there be, and what to expect with it?

- documentation
- wallet
- backup
- auth
- tracker
- mining
- exchange
- strategy

## What's in it for me

What would contributors to the project get out of doing so?

- Opt-out donation of 3% of all mined coins
- Donations accepted adevertised within the programs
- Distributed back to contributors
	- Based on weighted ratings and popularity of the modules that they contribute

## Conclusion

- Aims
	- Make cryptocurrencies mainstream, by making them more accessible
	- Ease the burden of managing multiple cryptocurrencies
	- Single go-to for all the different types of coins
	- Provide platform that encourages contribution in modular form
	- Decentralised distribution of packages
- Further
	- Ideas are still very raw
	- Please contribute ideas, ideas for implementation and architecture, etc

----

Like this idea enough to tip?

bitcoin:1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG
[! bitcoin:1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG ](https://chart.googleapis.com/chart?cht=qr&chl=bitcoin%3A1NWuxuKgTmG8ABMbMoVv4MTqxtfzBH9osG&choe=UTF-8&chs=200x200)
