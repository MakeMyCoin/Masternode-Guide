# Masternode-Guide

![Example-Logo](https://cdn.discordapp.com/attachments/478524354913763329/598380981183053824/overview.png)

# MakeMyCoin Masternode Setup Guide (Ubuntu 16.04)
***
## Required
1) **5000 MMCO coins**
2) **Local Wallet https://github.com/MakeMyCoin/MakeMyCoin/releases**
3) **VPS with UBUNTU 16.04**
4) **Putty https://www.putty.org/**
5) **Text editor on your local pc to save data for copy/paste**
***

***On your Local Wallet***
* Create an address with a label MN1 and send exactly 5000 MMCO to it. Wait to complete 6 confirmations on “ Payment to yourself “ created.

* Open the Debug Console ( Tools – Debug Console ) and type ***masternode genkey***.
You will then receive your private key, save it in a txt to use it later.
  ```
  Example:
          masternode genkey
          3k723KqiiqtiLH6y2ktjfwzuSrNucGAbagacdmCn1KnNEeQTJKf
* Still at Debug Console type ***masternode outputs*** and save txhash and outputidx on a txt
  ```
  Exemple:
          "txhash" : "19999c1a5623aa5b5830abff1a9feb6a682b75ee9fe22c647725a3gef42saa",
		         "outputidx" : 0

***On Putty***

* Once logged in your vps, *copy/past* each line one by one with *Enter*

	:arrow_forward: `wget -q https://github.com/MakeMyCoin/MakeMyCoin/releases/download/V1.0/MakeMyCoin_MN.sh`

	:arrow_forward: `bash MakeMyCoin_MN.sh`

* Let this run, and when prompted for a masternode key, copy the one you got previously (masternode genkey) and press enter.

Remember to do `MakeMyCoin-cli getblockcount` to check if VPS synced with chain

Do not close your terminal/ command prompt window at this point.

***Go back to your Local Wallet***

* Open the Masternode Configuration file (tools – open masternode configuration file) and add a new line (without #) using this template (bold needs to be changed) in the final save it and close the editor

**ALIAS VPS_IP**:12163 **masternodeprivkey TXhash Output**

		Example:
		MN1 125.67.32.10:12163 3k723KqiiqtiLH6y2ktjfwzuSrNucGAbagacdmCn1KnNEeQTJKf
		199999c1a5623aa5b5830abff1a9feb6a682b75ee9fe22c647725a3gef42saa 0

* Close and Re-open Local Wallet, and at Masternode Tab you will find your MN with status MISSING

***(For the next steps you need to have already 21 confirmation on “Payment to yourself “ created in first step)***

* Still on Masternode tab right click on the line of the MN with status MISSING and choose "Start Alias" for your Masternode change the status to ENABLE

NOTE: If for some reason the previous method doesn't work please do the follow

* Go to Debug Console type the following: ***startmasternode alias 0 (mymnalias)***

		Example:
		startmasternode alias 0 MN1
***

***Go back to Putty***

   :arrow_forward: `MakeMyCoin-cli masternode status`

You need to get **"status" : 4**

## Congratulations your MakeMyCoin node it's running
