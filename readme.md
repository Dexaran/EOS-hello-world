# Hello World contract for EOS 1.6x

Currently [Hello World](https://developers.eos.io/eosio-home/v2.3.0/docs/your-first-contract) turorial is outdated and if you will compile the code then it will not work on EOS mainnet.

Here is my tutorial for compiling and deploying "Hello World" contract on EOS mainnet (actual for EOS 1.6x and eos cdt 1.5x / Ubuntu 18.04). 

#### 1. Use proper version of EOSIO and EOSIO CDT software

Firs of all make sure that you have EOSIO cdt version 1.5.x and EOSIO 1.6.x. Do not use commands provided in tutorial. Build it from source https://github.com/EOSIO/eos/releases

#### 2. Make sure you have an account

`cleos wallet list` - show your wallets

If you don't have an account in `cleos` then it is necessary to import it. You need to sign up a EOS account with 12-character name first (you can follow [this instruction](https://medium.com/@dexaran820/creating-and-signing-up-eos-account-sending-receiving-transactions-14157b97c6e2)). Then we will import this already-existing account into the `cleos` and create an account entry there.
  
`cleos wallet create -n <account_name> --to-console` - create a new wallet entry. IMPORTANT: `<account_name>` must be 12-character name of your account.

My command looks like this:

`cleos wallet create -n dexaraniiznx --to-console`

Output of the command is shown at the screenshot below. Save the "password string" for your account becasue you need it to unlock the wallet ("PW5KhdWan1ySa5nAAefHSadmeNuhBHXh1WV6HzGknTQiyeCPR9wf9" in my example).

![OUT1](https://github.com/Dexaran/EOS-hello-world/blob/master/images/OUT1.png)

Run:

`cleos wallet unlock -n <account_name>`

Then run:

`cleos wallet import -n <account_name> --private-key <private_key>` to import your private key.

![OUT2](https://github.com/Dexaran/EOS-hello-world/blob/master/images/OUT2.png)

Now you have a ready-to-go account entry in `cleos`.

#### 3. Create the smart-contract in proper folder

IMPORTANT: You must name contracts, folders and accounts according to [EOS naming conventions](https://developers.eos.io/eosio-cpp/v1.3.2/docs/naming-conventions). It is very important to keep folder/file/classe names exactly as written in this example, otherwise compilation may fail.

Create `contract` folder. Then create `contract.cpp` file inside the `contract` folder. It is important that this folder and file have the same name.

Write the following code in the `contract.cpp` file:
```cpp
#include <eosiolib/eosio.hpp>
#include <eosiolib/print.hpp>

using namespace eosio;

class [[eosio::contract("contract")]] hello : public contract {
  public:
      using contract::contract;

      [[eosio::action]]
      void hi( name user ) {
         print( "Hello, ", user);
      }
};

EOSIO_DISPATCH( hello, (hi))
```

In terminal navigate to the folder where the `contract.cpp` file is located.

`cd <path_to_your_folder>/contract`

#### 4. Compiling the contract

Run:

`eosio-cpp -o <contract_name>.wasm <contract_name>.cpp --abigen` where `<contract_name>` is the name of your contract which is similar to the name of the folder where the contract is located.

In my example this command is:

`eosio-cpp -o contract.wasm contract.cpp --abigen`

The result is shown at the image below:

![OUT3](https://github.com/Dexaran/EOS-hello-world/blob/master/images/OUT3.png)
