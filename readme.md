# Hello World contract for EOS 1.6x

Currently [Hello World](https://developers.eos.io/eosio-home/v2.3.0/docs/your-first-contract) turorial is outdated and if you will compile the code then it will not work on EOS mainnet.

Here is my tutorial for compiling and deploying "Hello World" contract on EOS mainnet (actual for EOS 1.6x and eos cdt 1.5x / Ubuntu 18.04). 

#### 1. Use proper version of EOSIO and EOSIO CDT software

Firs of all make sure that you have EOSIO cdt version 1.5.x and EOSIO 1.6.x. Do not use commands provided in tutorial. Build it from source https://github.com/EOSIO/eos/releases

#### 2. Make sure you have an account

`$ cleos wallet list` - show your wallets

`$cleos wallet create -n <account_name> --to-console` - create a new wallet entry. IMPORTANT: `<account_name>` must be 12-character name of your account.

My command looks like this:

`cleos wallet create -n dexaraniiznx --to-console`

Output of the command is shown at the screenshot below. Save the "password string" for your account becasue you need it to unlock the wallet ("PW5KhdWan1ySa5nAAefHSadmeNuhBHXh1WV6HzGknTQiyeCPR9wf9" in my example).
