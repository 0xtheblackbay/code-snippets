## Introduction

This program allows you to create an Ethereum Virtual Machine (EVM) compatible public address, private key, and mnemonic. However, it requires basic development knowledge for setting up the environment to run the program. Once set up, you can use it to securely store and manage your Ethereum and other ERC-20 tokens.
So instead of clreating your wallet online with metamask , now you will be able to create it offline

## Disclaimer

This program is distributed in the hope that it will be useful, without warranty of any kind, either expressed or implied, including, but not limited to, the implied warranties of merchantability and fitness for a particular purpose.
You use this program entirely at your own risk. The author will not be liable for any damages arising from the use of this program.

## License

This program is free for personal and commercial use. yo umay do whatever you want with it.

## Credits

- Old time when search was done via Google.
- [TheFalconX2022](https://github.com/FalconX2022) for the google digging.

## Requirements

The program has been tested with NodeJS 16.20.0 You can [Download @ NodeJS](https://nodejs.org/en/download/) or, alternatively, install nvm to manage your NodeJS version more dinamically. You can find NVM [here](https://github.com/nvm-sh/nvm).

Details about execution:
```sh
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> node --version
v16.20.0
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> npm -v
8.19.4
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> 
```

## dependencies

Running under the premises stated above (NodeJS 16.20.0, npm 8.19.4), program runs with no detected vulnerabilities and can be executed offline once installed.

```json
  "dependencies": {
    "ethers": "^5.7.2",
    "log4js": "^6.4.1",
    "secure-env": "1.2.0",
    "toml": "^3.0.0"
  }
```
## How to run this

1. Clone The Black Bay *code-snippets* repo:
```sh
git clone git@github.com:0xtheblackbay/code-snippets.git
```

2. Navigate to the corresponding code-snippet folder:
```sh
cd code-snippets/node-js/wallet
```

3. You should see the followwing structure:
```sh
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> tree -a ./
./
├── .config
├── create.js
├── env
├── .gitignore
├── package.json
├── README.md
├── restore.js
└── utils
    └── secureEnv.js

1 directory, 9 files
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet>
```

4. Run the following command to install the dependencies:
```sh
npm i
```

The output should resemble something similar to this:
```sh
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> npm i

added 59 packages, and audited 60 packages in 24s

32 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet>
```

5. once the dependencies have been installed, create your .env file and encrypt it as per [secure your environment](#secure-your-environment).

6. with your encrypted file available (.env.enc), you should be able to invoke any of the two available features *wallet* currently offers:
    - [create](#create)
    - [restore](#restore)

> @dev: the **restore** operation looks for an existing SEED in the .env.enc file, failing to find this, program will fail.

## operations

### Create

Use this script to create new seed phrase.

It will give you the details of as many accounts as you have defined in the .config file.

The code-snippet *wallet* comes predefined to work with 3 accounts. If you want a different number then adjust them in the .config file **before** running the corresponding program.

```toml(.config)
NUMBER_OF_ACCOUNTS=3
```
> **@EVERYONE**: don't forget to save the seed phrase from the output, without it you wont be able to recover your wallet and your funds.

1. To create a new wallet run the following command:
```sh
npm run create
```

The output you'll get will look something similar to this one:

```sh
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> npm run create

> wallet@1.0.0 create
> node create.js

[2023-05-28T15:19:11.769] [DEBUG] create-script - loading configuration.
[2023-05-28T15:19:12.041] [DEBUG] create-script - Generating a random wallet with 3 accounts...
[2023-05-28T15:19:12.304] [DEBUG] create-script - Your seed phrase is: phrase tip donkey author square outside smoke dad memory switch surge kid
[2023-05-28T15:22:09.841] [DEBUG] restore-script - Account 0 details:
 Public Address: 0x1b1e71Be3C6842Bbe6D37647544A351E29451e64
 Private Key: 0xb4381acb60d7429f8f69380d3dbaa84a2dc4bdb9c677408ce911deee1f654dd7
[2023-05-28T15:22:09.923] [DEBUG] restore-script - Account 1 details:
 Public Address: 0xCB9Fa2A94181517e214A57199E8A114863AcD9Bf
 Private Key: 0x59eb1ae9f58dde743409b2d236ab9f7b5984c849356863d6bf53b5c4970c35d0
[2023-05-28T15:22:10.020] [DEBUG] restore-script - Account 2 details:
 Public Address: 0xF0F41E75e2fA09365f31d294afD2ADa0Cf621A3C
 Private Key: 0x80ec3b973978b7ef076a092adf62b9e62f9cee2d8082e8266f8d67be68646497
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet>
```

### Restore

Use this script in case you already have a seed phrase and you want to remember its associated private keys or public addresses.

It will give you the details of as many accounts as you have defined in the .config file.

The code-snippet *wallet* comes predefined to work with 3 accounts. If you want a different number then adjust them in the .config file **before** running the corresponding program.

```toml(.config)
NUMBER_OF_ACCOUNTS=3
```

To run the restoration script, proceed as follows:

1. Copy the env filefrom the `/` folder and change its name to .env.

2. Replace the `your_seed_goes_here` text with the seed phrase you want to recover and follow steps in [secure your .env file](#secure-your-environment).

3. Assuming you have chosen `MY_PASSWORD` as the encryption key for your .env file, run the following command:

```sh
npm run restore MY_PASSWORD
```

The output you'll get will look something similar to this one:

```sh
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> npm run restore MY_PASSWORD

> wallet@1.0.0 restore
> node restore.js MY_PASSWORD

[2023-05-28T15:22:09.311] [DEBUG] restore-script - loading configuration.
[2023-05-28T15:22:09.327] [DEBUG] restore-script - loading secure environment.
[2023-05-28T15:22:09.335] [DEBUG] restore-script - Your seed phrase is: phrase tip donkey author square outside smoke dad memory switch surge kid
[2023-05-28T15:22:09.336] [DEBUG] restore-script - Restoring 3 accounts...
[2023-05-28T15:22:09.841] [DEBUG] restore-script - Account 0 details:
 Public Address: 0x1b1e71Be3C6842Bbe6D37647544A351E29451e64
 Private Key: 0xb4381acb60d7429f8f69380d3dbaa84a2dc4bdb9c677408ce911deee1f654dd7
[2023-05-28T15:22:09.923] [DEBUG] restore-script - Account 1 details:
 Public Address: 0xCB9Fa2A94181517e214A57199E8A114863AcD9Bf
 Private Key: 0x59eb1ae9f58dde743409b2d236ab9f7b5984c849356863d6bf53b5c4970c35d0
[2023-05-28T15:22:10.020] [DEBUG] restore-script - Account 2 details:
 Public Address: 0xF0F41E75e2fA09365f31d294afD2ADa0Cf621A3C
 Private Key: 0x80ec3b973978b7ef076a092adf62b9e62f9cee2d8082e8266f8d67be68646497
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> 
```

## secure your environment  

The project uses an environment file to handle sensible data (the SEED phrase, in this case), which require access through your application environment.

To handle this type of files in a more secure manner, we can encrypt them, ensuring that other activities, like the installation of a malicious or compromised npm package cannot access to this sensible information.

This code-snippet has incorporated that feature by implementing [secure-env](https://github.com/kunalpanchal/secure-env), a tool that behaves similarly to the well known dot-env but with an encrypted instance of the file, instead of a clear one.

In order to encrypt your .env file (use the env file provided as template), proceed as follow:  

> @dev: To reduce risks ad-maximum, *follow the securing procedure* **AFTER** installing the project dependencies, and *delete the un-encrypted .env file* **BEFORE** installing or executing any associated program.

1. ensure you have installed the project dependencies as per [How to run this](#howto-run-this).  

2. copy `env` as `.env` and complete the required fields. It would end looking something similar to the following example:

```toml(.env)
SEED=phrase tip donkey author square outside smoke dad memory switch surge kid
```

3. execute `npm run generate-env YOUR_PASSWORD`. 

```sh  
npm run generate-env YOUR_PASSWORD

> wallet@1.0.0 generate-env  
> secure-env .env -s YOUR_PASSWORD  

Secure-env :  INFO The Environment file ".env" has been encrypted to ".env.enc".  
Secure-env :  WARNING Make sure to delete ".env" for production use.  
```  
4. list the content of the folder, to confirm your new encrypted file is there.

```sh
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet> tree -a -L 1 ./
./
├── .config
├── create.js
├── .env
├── env
├── .env.enc
├── .gitignore
├── node_modules
├── package.json
├── package-lock.json
├── README.md
├── restore.js
└── utils

2 directories, 10 files
tbb@tbb:~/git/tbb/code-snippets/node-js/wallet>
```

5. Remember to **delete** your original *.env* file when deploying on PRODUCTION environments. :)  

## other resources

- [secure-env](https://github.com/kunalpanchal/secure-env).