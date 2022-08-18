# **Introduction**

## **Overview**

This app allows one to access their crypto wallets using different cryptocurrencies and allows the transfer and receive of cryptocurrency as well as displaying their values in different currencies.

# **Environment**

## **Getting Started**

Ensure you have installed the following:

- Ionic
- Nodejs
- Android Studio
- Java SDK
- Gradle

Link to setting up Ionic:

[Ionic Framework setup](https://ionicframework.com/docs/intro/cli)

Link to download Android Studio:

[Android Studio](https://developer.android.com/studio)

Setting up on Windows:

Search "Edit System variable" to open the "System Properties" settings and click on "Environment Variables".

<img src="https://user-images.githubusercontent.com/60563965/184846251-53fe6992-708c-49cd-910e-513a1cce6077.png" alt="System environment" title="System environment" width="60%">

Add the 2 variables into "System variables" where the file path is to the Sdk file in the downloaded Android Studio folder.

<img src="https://user-images.githubusercontent.com/60563965/184846699-adf4f72a-8d35-4846-a9fb-178a8e8bacf8.png" alt="System variables" title="System variables" width="60%">  

&nbsp;

# **Starting Out**

## **Clone the project from GitHub**

[Source code](https://github.com/jaylim/mobile-web3/tree/main)

## **Running the app to debug**

Navigate into the project directory and type into the terminal

``` 
ionic serve
```

The app will be opened in the browser and be found at:

[http://localhost:8100/](http://localhost:8100/)

## **To run the app on Android:**

In the project directory type into the terminal

**might be wrong**
```
 npx cap sync android
 npx cap open android 
```

The app should open in Android Studio where you can run the app on an emulator or on an Android device.

## **To run the app on IOS:**

…

# **Directories**

`/android` - contains the files to allow the app to run on Android devices   
`/e2e` - the end to end folder  
`/resources` - folder containing the resources for the app  
`/src` - the folder for the source files  

## **The source code can be found in in the folder:**
**`/mobile-web3/src/app`**

&nbsp;

# **Opening the app for the first time**
Upon opening the app for the first time the user will be greeted with a splash screen. 
&nbsp;

<img src="https://user-images.githubusercontent.com/60563965/185289195-18655573-78e3-40aa-9e17-fb4360b6d1e8.png" alt="splash1" height="270px">
<img src="https://user-images.githubusercontent.com/60563965/185289414-ff05cdda-02de-4d43-9860-5b8e650a5db4.png" alt="splash2" height="270px">
<img src="https://user-images.githubusercontent.com/60563965/185289684-a619b2ce-e2b9-4398-b453-4e184fa36688.png" alt="splash3" height="270px">
<img src="https://user-images.githubusercontent.com/60563965/185289762-5e496b93-f395-475f-85dd-c4213994189b.png" alt="splash4" height="270px">

&nbsp;

### **The files for the splash screen page will be found in:**
**`/mobile-web3/src/app/home`**
- The front end is found in - `/mobile-web3/src/app/home/home.page.html`  
- The app logic is found in - `/mobile-web3/src/app/home/home.page.ts`

<details>
    <summary>Code documentation</summary>

Upon initialization, it will initialize the web3 functions. Upon construction it set the default network and the default currency in the local storage and set the array of languages used in the `languages` field.

- **`pushWelcome()`**  
  - Opens the welcome page.

- **`changeLanguage()`**  
  - Translates and set as default language based on `defaultLanguage` field.

</details>
&nbsp;

The splash screen will have 4 slides and the last slide contains an option to change the language and a start button that will open the welcome page.

### **The files for the change language page will be found in:**  
**`/mobile-web3/src/app/change-language`**
- The front end is found in - `/mobile-web3/src/app/change-language/change-language.page.html`  
- The app logic is found in - `/mobile-web3/src/app/change-language/change-language.page.ts`


<details>
    <summary>Code documentation</summary>

Upon initialization an array of languages are added where each language is in the form of an array where each contains 2 strings, one for the title and one of the code.

- **`changeLanguage(p)`**  
  - Changes the `default_language` value in the local storage.

- **`dismissModal()`**  
  - Closes the modal.

</details>
&nbsp;

Upon opening the welcome page the user will be greeted with 2 options, one to create a wallet and one to import a wallet. All options will first require the user to input a pin and input the pin again for a second time to confirm.

<img src="https://user-images.githubusercontent.com/60563965/185290168-b2fb365a-d90c-4313-8e20-9f591de92cbb.png" alt="welcome" width="40%">

### **The files for the welcome page will be found in:**  
**`/mobile-web3/src/app/welcome`**

- The front end is found in - `/mobile-web3/src/app/welcome/welcome.page.html`  
- The app logic is found in - `/mobile-web3/src/app/welcome/welcome.page.ts`

<details>
    <summary>Code documentation</summary>

Upon construction, check if there's a wallet, if yes, open the tabs page, else set the `showPage` field to true.

- **`pushImportPage()`**  
  - Opens the import wallet page to import a wallet.

- **`pushCreateWalletPage()`** 
  - Opens the mnemonic page to create a wallet.

</details>
&nbsp;

### **The files for the create wallet page will be found in:**  
**`/mobile-web3/src/app/mnemonic`**

- The front end is found in - `/mobile-web3/src/app/mnemonic/mnemonic.page.html`  
- The app logic is found in - `/mobile-web3/src/app/mnemonic/mnemonic.page.ts`

<details>
    <summary>Code documentation</summary>

Upon initialization it will generate a mnemonic. Upon construction sets the translation of the text and sets the derivation paths in the local storage. If there is a pin in the storage, get the wallet path from the local storage and store in the relevant fields, and set the current network in the field.

- **`generateMnemonic()`**  
  - Sets the `strength` variable based on the value of `value_selected` field. Generates a mnemonic with the `generateMnemonic()` function from bip39 using a word list and the `strength` variable and assign to the `mnemonic` field. Use split the mnemonic into an array and use to to call the `arrangeMnemonic()` function.

- **`copyMnemonic()`**  
  - Copies the mnemonic stored in the field to the clipboard and calls the `toastMessage()` function to display a success message as a toast.

- **`arrangeMnemonic()`**  
  - Arranges the list of mnemonics in a grid of 3 columns.

- **`getAddress(mnemonic)`**  
  -Gets the address of the wallet using the mnemonic input as the parameter and is stored in the local storage and storing the encryption keys in the storage.

- **`handleInput(input)`**  
  - `input` - a string representing the corresponding button clicked.  
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add `input` to `pin`, if the length of `pin` is 4, delay for 0.1s and sets `verifyPin` field to true to verify the pin.

- **`handleConfirmInput(input)`**  
  - `input` - a string representing the corresponding button clicked.  
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add `input` to `confirmPin`, if the length of `confirmPin` is 4, delay for 0.1s and checks if `confirmPin` is same as `pin`, if it is sets `createPin` and `verifyPin` fields to false and finish, else calls `presentAlert()`, set `verifyPin` to false, and `confirmPin` and `pin` to an empty string and finish.

- **`presentAlert()`**  
  - Presents an alert to inform the user the pin for confirmation doesn't match.

- **`presentAlert2FA()`**  
  - Presents an alert, has 2 buttons, one for yes and opens the **`two-factor-authentication`**page, and one for no which saves the wallet information in local storage and opens the `dashboard` page.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

</details>
&nbsp;

The import wallet option opens the import wallet page and gives an option to import with private key and import with mnemonic.

### **The files for the import wallet page will be found in:**  
**`/mobile-web3/src/app/import-wallet`**

- The front end is found in - `/mobile-web3/src/app/import-wallet/import-wallet.page.html`  
- The app logic is found in - `/mobile-web3/src/app/import-wallet/import-wallet.page.ts`  

<details>
    <summary>Code documentation</summary>

Upon initialization, it will call the `arrangeMnemonic()` function with an empty string, and on construction it will set up the array of networks in the `networks` field and call the `setTranslation()` function.

- **`handleInput(input)`**  
  - `input` - a string representing the corresponding button clicked.  
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add `input` to `pin`, if the length of `pin` is 4, delay for 0.1s and sets `verifyPin` field to true to verify the pin.

- **`handleConfirmInput(input)`**  
  - `input` - a string representing the corresponding button clicked.  
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add `input` to `confirmPin`, if the length of `confirmPin` is 4, delay for 0.1s and checks if `confirmPin` is same as `pin`, if it is sets `createPin` and `verifyPin` fields to false and finish, else calls `presentAlert()`, set `verifyPin` to false, and `confirmPin` and `pin` to an empty string and finish. 

- **`doContinue()`**  
  - Submits the mnemonic and checks if the submitted mnemonic is valid.

- **`submitPKey()`**  
  - Checks if the network used is Solana Network, if it is use to private key from `myPrivateKey` field to login to Solana with necessary information, else use the private key from `myPrivateKey` to log into Ethereum with the necessary information.

- **`arrangeMnemonic()`** 
  - Arranges the list of mnemonics in a grid of 3 columns.

- **`pasteMnemonic()`**  
  - Pastes the contents of the clipboard in the form of a space-delimited list to `list_mnemonic` and arrange the mnemonic with the `arrangeMnemonic()` function.

- **`switchValue(value)`**   
  - Assigns the `value` parameter to the `value_selected` field and call the `arrangeMnemonic()` function with an empty string as parameter.

- **`importPKey(ev)`**  
  - Assigns the `myPrivateKey` field with the `ev` parameter.

- **`getAddress(mnemonic)`**  
  - Gets the address of the wallet using the mnemonic input as the parameter and is stored in the local storage and storing the encryption keys in the storage.

- **`presentAlert()`**  
  - Presents an alert to inform the user the pin for confirmation doesn't match.

- **`presentAlert2()`**  
  - Presents an alert to inform the user the pin inputted is invalid and they have to try again.

- **`presentAlert2FA()`**  
  - Presents an alert, has 2 buttons, one for yes and opens the **`two-factor-authentication`** page, and one for no which saves the wallet information in local storage and opens the `dashboard` page.

- **`changeNetwork()`**  
  - Changes the `isSolanaNetwork` to the opposite of the current value.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.
 
- **`delay(ms)`**  
  - Adds a delay for `ms` amount of milliseconds.

</details>
&nbsp;

After creating or importing a wallet the dashboard page will be opened.

# **Opening the app on subsequent times**  
The user will be greeted with a pin page to input the pin to access the account, there is an option to reset the pin which opens a different page.

### **The files for the pin page will be found in:**  
**`/mobile-web3/src/app/pin`**

- The front end is found in - `/mobile-web3/src/app/pin/pin.page.html`  
- The app logic is found in - `/mobile-web3/src/app/pin/pin.page.ts`  

<details>
    <summary>Code documentation</summary>

Upon initialization, call the `checkCountDown()` function.

- **`pushResetPinPage()`**  
  - Opens the **`reset-wallet-pin`** page.

- **`handleInput(input)`**  
  - `input` - a string representing the corresponding button clicked.  
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add `input` to `pin`, if the length of `pin` is 4, checks if the pin is the same as the pin stored in local storage. If the pin matches, opens the `dashboard` page, else increases the `incorrectPinCounter` field. If the counter is a multiple of 3, block the pin for a set duration of time, else call `presentAlert()` to present the alert.

- **`countDown(duration)`**  
  - Sets the countdown time and updates the time left in the html every 1s.

- **`presentAlertPinBlocked(duration)`**  
  - Presents an alert showing the amount of time left when the pin has been blocked for multiple incorrect attempts.

- **`presentAlert()`**  
  - Presents and alert showing the amount of attempts remaining before the pin gets blocked.

- **`checkCountDown()`**  
  - Get the time when the countdown ends and set it as a variable `endTime`, and set the current time to the variable `now`. The variable `distance` will be the difference between `endTime` and `now`. If `now` is before `endTime`, call the `countDown()` function with `distance` to set the remaining time left. If `now` is the same or after `endTime` the countdown timer will stop showing.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

</details>
&nbsp;

### **The files for the reset pin page will be found in:**  
**`/mobile-web3/src/app/reset-wallet-pin`**

- The front end is found in - `/mobile-web3/src/app/reset-wallet-pin/reset-wallet-pin.page.html`  
- The app logic is found in - `/mobile-web3/src/app/reset-wallet-pin/reset-wallet-pin.page.ts` 

<details>
    <summary>Code documentation</summary>

Upon initialization, it will call the `setTranslation()` function to set the text to the target language. Checks if the user has 2 factor authentication activated and display the relavent alert

- **`checkTwoFactorAuthenticationCode(userToken)`**  
  - Checks the validity of the 2 factor authenticaition.

- **`handleInput(input)`**  
  - `input` - a string representing the corresponding button clicked
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add “input” to “pin”, if the length of “pin” is 4, delay for 0.1s and sets “verifyPin” field to true to verify the pin.

- **`handleConfirmInput(input)`**  
  - `input `- a string representing the corresponding button clicked.
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add `input` to `confirmPin`, if the length of `confirmPin` is 4, delay for 0.1s, check if the pin is correct, if it is wrong, present an alert. If the pin is correct, get the private key from the storage and encrypt the private keys.

- **`delay(ms)`**  
  - Adds a delay for `ms` amount of milliseconds.

- **`presentAlert()`**  
  - Presents an alert informing the user the pin is incorrect.

- **`presentSuccessAlert()`**  
  - Presents an alert informing the user the pin is correct.

- **`presentAlert2FA()`**  
  - Presents an alert to give the user an option to set up 2 factor authentication.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.
</details> 
&nbsp;

# **Entering the app**   
The user will be greeted by the dashboard that show the current balance as well as the equivalent value of the balance.

<img src="https://user-images.githubusercontent.com/60563965/185352031-e309c36b-3de1-40c5-add0-32235bc8380a.png" alt="dashboard" width="40%">

### **The files for the dashboard page will be found in:**  
**`/mobile-web3/src/app/dashboard`**

- The front end is found in - `/mobile-web3/src/app/dashboard/dashboard.page.html`  
- The app logic is found in - `/mobile-web3/src/app/dashboard/dashboard.page.ts`

<details>
    <summary>Code documentation</summary>


A tab in the tabs page. Upon initialization, it will call the `setTranslation()` function. After it will get the token list, coins and icon list from the local storage and assign it to fields. The wallet address will be truncated. The `updateETHPrice()` and `getGlobalTokenList()` functions will be run.

- **`changeNetwork()`**  
  - Opens a modal to change networks.

- **`changeAccount()`**  
  - Opens a modal that provides the changing account service.

- **`copyAddr()`**  
  - Copies the contents of the `walletAddress` field to the clipboard, then calls the `toastMessage()` function with the `successCopyMessage` field as the parameter.

- **`addAccount()`**  
  - Calls the `alertAddAccount()` function.

- **`mainPushSendPage()`**  
  - Opens the **`send-transaction`** page.

- **`pushReceivePage(symbol, balance)`**  
  - Opens the **`receive-transaction`** page, with the parameters as extras for the navigation.

- **`pushSendPage(symbol, balance, address, usd)`**  
  - Opens the **`send-transaction`** page, with the parameters as extras for the navigation.

- **`doRefresh(refresher)`**  
  - Calls the refresher and calls the `updateETHPrice()` and `getGlobalTokenList()` functions and completes the refreshing process.

- **`truncateString(str, num)`**  
  - `str` - the string to be truncated.  
  - `num` - number of characters to be truncated.  
  - The function truncates the given string `str` leaving only the first `num` amount of characters and leaving "..." after. If the given string is shorter or the same length than the amount of characters of `num` the string will be returned as it is.

- **`truncateAddress(str)`**
  - `str` - the address to be truncated.  
  - Checks if the address `str` is longer than 20 characters, if it is, take the 1st 4 characters and the last 4 characters and concatenate them with "..." in between.

- **`toFixedDown(value, digit)`**  
  - `value` - the number that will be rounded.  
  - `digit` - the amount of decimal places to be rounded to, only works with whole numbers.  
  - Rounds the `value` to the amount of decimal places specified by the value of `digit` and will always round down the value.

- **`toastMessage(data)`**  
  - `data` - a string that will be presented in the toast.  
  - A toast will be created and will last for 1 seconds and present `data` as the message.

- **`getETHBalance()`**  
  - Checks if the `currentNetwork` field is `Solana Mainnet` if it is, gets the balance using the wallet address from `walletAddress`. The `tmp` variable is then created and will be assigned the balance divided by `LAMPORTS_PER_SOL`, and the `balanced_ETH` field from the local storage will be set with `tmp` after it gets stringfied.  
  - If the current network is not Solana Mainnet, the `tmpAddress` variable will be created and be assigned with `w_address` from the local storage. The `balance_ETH` field will be assigned with the balance.  
  - After setting `balance_ETH` in the local storage for both the if and else case, the `balance_ETH` field will be assigned with the same field from the local storage and the `value_ETH` field will be assigned with the number of `balance_ETH` multiplied with the number of `price_ETH`, and if `value_ETH` is not a number it will be set to 0.

- **`updateETHPrice()`**  
  - Updates the price of ETH in the current selected currency.

- **`getGlobalTokenList()`**  
  - Check if the `currentNetwork` field is "BSC Mainnet" if it is, set the `currentTokenListToUse` field to `myTokenBSC`. Then try calling the API.
    - API link - <ins>`https://tokens.pancakeswap.finance/pancakeswap-extended.json`</ins>   
  - If the `tokens` array in the api has a length more than 0, assign an empty array to the `allTokenList` field. Then loop through the `tokens` array, adding each entry into the `allTokenList` array. Then call the `removeExistingToken()` and `removeExistingFavouriteToken()` functions with the `coins` field as the parameter, and set the `allTokensBSC` field in the storage with the `allTokenList` field as a string.  
  - If an error happens, a variable `allTokens` will be assigned with the `allTokensBSC` field from the storage after being parsed, and if `allTokens` is not null, and array will be formed from `allTokens` and assigned to the `allTokenList` field.  
  - Then try to call the api for getting the token of the given wallet address. If the length of the `coins` array in the API is more than or equal to 0, call the `tidyTokenInfo()` function with the `data.items` from the api as the parameter.   
    - API link - <ins>`https://api.covalenthq.com/v1/56/address/`</ins>, and uses the `walletAddress` and `currentCurrency` fields as the query parameters.  
  - If the `currentNetwork` field is not `BSC Mainnet`, repeat the process for "Solana Mainnet".
    - API for token list - <ins>`https://cdn.jsdelivr.net/gh/solana-labs/token-list@latest/src/tokens/solana.tokenlist.json`</ins>  
    - API for wallet address - <ins>`https://api.covalenthq.com/v1/1399811149/address/`</ins>, and uses the `walletAddress` and `currentCurrency` fields as the query parameters. 

- **`removeExistingToken(tokenList)`**  
  - `tokenList` - an array of tokens.  
  - Removes the tokens from the `allTokenList` array that matches an entry in `tokenList`.

- **`removeExistingFavouriteToken(tokenList)`**  
  - `tokenList` - an array of tokens.   
  - Removes the favorite tokens from the `allFavouriteTokenList` array that matches an entry in `tokenList`.

- **`tidyTokenInfo(tokenList)`**  
  - `tokenList` - an array of tokens.  
  - Loops through `tokenList` and checks if the current network in the `currentNetwork` field matches the corresponding token in the `contract_name` field of `tokenList`, if it is skip to the next iteration, else set the relevant fields about the tokens in the local storage and storage.

- **`getDataUri(targetUrl, tokenSymbol)`**  
  - `targetUrl` - the url to get the file.  
  - `tokenSymbol` - the filename without the extension  
  - Gets the file from the target url and returns the downloaded file, if an error occurs, it will be logged to the console.

- **`delay(ms)`**  
  - Adds a delay for `ms` amount of milliseconds.

- **`alertAddAccount()`**  
  - Creates an alert for adding an account, creating an account and closing the alert.

- **`createNewAccount()`**  
  - Sets the `accountList` field to an empty array. Checks if the current network is either BSC, ETH or MATIC Mainnets, if yes, change the relevant account information in the local storage and as well as change the `derivationPath` field. If the current network is Solana Mainnet, change the `derivationPath` field.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

</details>
&nbsp;

There is a button that opens a modal window that is for changing the network, changing account. There are also button that opens the page to send currency and receive currency. There is also a menu on the top right.


### **The files for the change network window will be found in:**  
**`/mobile-web3/src/app/change-network`**

- The front end is found in - `/mobile-web3/src/app/change-network/change-network.page.html`  
- The app logic is found in - `/mobile-web3/src/app/change-network/change-network.page.ts`

<details>
    <summary>Code documentation</summary>

Upon initialization the `setTranslation()` function is called. Upon construction an array of networks will be added to the `networkList` array, names of each network will be added into the array. The `selectedNetwork` field will be assigned with `current_network` from the local storage.

- **`changeNetwork(p)`**
  - Changes the network and store in local storage. If there is no `walletAddress` then the `alertEmptyWalletAdress()` function is called, else variables from the local storage will be changed and variables will be removed from the storage.

- **`dismissModal()`**  
  - Closes the modal.

- **`alertEmptyWalletAdress()`**  
  - Creates an alert with header, subheader, and messages based on the fields. Also contains 3 buttons, one button for creating a wallet that redirects to the **`mnemonic`** page with the role of 'ok', one button to import a wallet that redirects to the **`import-wallet`** page with the role of 'ok' and one button to cancel and assigns the `currentNetwork` field to the `selectedNetwork`.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

</details>
&nbsp;

### **The files for the change account window will be found in:**  
**`/mobile-web3/src/app/change-account`**

- The front end is found in - `/mobile-web3/src/app/change-account/change-accountin.page.html`  
- The app logic is found in - `/mobile-web3/src/app/change-account/change-account.page.ts`

<details>
    <summary>Code documentation</summary>

Upon initialization, get the account list and private key list from the local storage.  

- **`changeAccount(index)`**  
  - Changes the account to the account of the given index.

- **`dismissModal()`**  
  - Closes the modal.  

</details>
&nbsp; 

### **The files for the send transaction page will be found in:**  
**`/mobile-web3/src/app/send-transaction`**

- The front end is found in - `/mobile-web3/src/app/send-transaction/send-transaction.page.html`  
- The app logic is found in - `/mobile-web3/src/app/send-transaction/send-transaction.page.ts`

<details>
    <summary>Code documentation</summary>

Upon initialization, it will call the `setTranslation()` function to set the text to the target language. Import information from the local storage to the field. Call the `checkCountDown()` function to check if the countdown is over. If the current network is not Solana, call the `getGasFeeEstimate()` function to get an estimate of the gas fee, else get the private key for solana from the local storage and store it in the `solanaPrivKey` field.  

- **`getGasFeeEstimate()`**  
  - Check if the network is BSC, if yes, call the api to get the gas fee for "fast", "average" and "slow".
    - API link - <ins>`https://api.bscscan.com/api?module=gastracker&action=gasoracle&apikey=G5FQSQ8C4GP129JF8PZGBVTGJ89PCQ8F8R`</ins>

- **`checkCountDown()`**  
  - Check if the count down timer has finished.  
  - Get the time when the countdown ends and set it as a variable `endTime`, and set the current time to the variable `now`. The variable `distance` will be the difference between `endTime` and `now`. If `now` is before `endTime`, call the `countDown()` function with `distance` to set the remaining time left. If `now` is the same or after `endTime` the countdown timer will stop showing.

-  **`scanQR()`**  
  - Uses the barcode scanner plugin and opens the camera to scan a QR code. Check the address of the QR code, and finish scanning.

- **`sendAllBalance()`**  
  - Sends the payment as long as the current value is less than or equals to the balance.

- **`countDown(duration)`**  
  - Sets the countdown time and updates the time left in the html every 1s.

- **`handleInput(input)`**  
  - `input` - a string representing the corresponding button clicked.  
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add `input` to `pin`, if the length of `pin` is 4, presents a loading screen for verifying the pin. Checks if the pin is the same as the pin stored in local storage. If the pin matches, opens the **`dashboard`** page, else increases the `incorrectPinCounter` field. If the counter is a multiple of 3, block the pin for a set duration of time, else call `presentAlert()` to present the alert. Then closes the loading screen.

- **`presentAlertPinBlocked(duration)`**  
  - Presents an alert showing the amount of time left when the pin has been blocked for multiple incorrect attempts.

- **`presentAlert()`**  
  - Presents an alert showing the amount of attempts remaining before the pin gets blocked.

- **`presentNoTokenAccountAlert()`**   
  - Presents an alert informing the user that there is no token account and gives the option to create a token account or cancel.

- **`presentsCreatedTokenAccountAlert()`**  
  - Alerts after a token account is created and has the option of creating a transaction.

- **`checkAddress(ev)`**  
  - Checks the validity of the given address `ev`.

- **`updateAmountToSend(ev)`**  
  - Checks if the amount is enough to be sent, if the current amount is less than the balance, call the `updateValue()` function with the amount to send and set the `insufficientBalance` field to false, else set the `insufficientBalance` field to true.

- **`updateValue(tokenAmount)`**  
  - Updates the value of the token in USD.

- **`toFixedDown(value, digit)`**  
  - `value` - the number that will be rounded.
  - `digit` - the amount of decimal places to be rounded to, only works with whole numbers.
  - Rounds the `value` to the amount of decimal places specified by the value of `digit` and will always round down the value.

- **`openBrowser(transactionHash)`**  
  - Opens a browser with the corresponding network that the transaction was done in to display the transaction.

- **`shareReceipt()`**  
  - Captures a screenshot and opens a modal to allow sharing the screenshot to other apps.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

- **`backToRoot()`**  
  - Changes to the **`dashboard`** page.

- **`toConfirmSend()`**  
  - Sets the `enterPin` field to be true.

- **`createTransaction()`**  
  - Opens a loading screen and process the amount that will be sent.

- **`createTokenAccount()`**  
  - Opens a loading screen and process the creation of the token account.

- **`sendTransaction()`**  
  - Opens a loading screen and process the tokens to be sent.

- **`toBaseUnit(value, decimals, BN)`**  
  - Converts a number into a big number.

- **`presentAlertTransactionFailed()`**  
  - Presents an alert informing the failure in the transaction. Has a button with the 'ok' role that calls the `backToRoot()` function to return to the `dashboard` page.

</details>
&nbsp;

### **The files for the receive transaction page will be found in:**  
**`/mobile-web3/src/app/receive-transaction`**

- The front end is found in - `/mobile-web3/src/app/receive-transaction/receive-transaction.page.html`  
- The app logic is found in - `/mobile-web3/src/app/receive-transaction/receive-transaction.page.ts`

<details>
    <summary>Code documentation</summary>


Upon initialization, it will call the `setTranslation()` function to set the text to the target language. Sets the `t_symbol` field to the corresponding network if it's Ethereum, BSC or Polygon, else it will be left as undefined. Set the `t_balance` field to the balance stored in the local storage, if there's no balance, leave `t_balace` as undefined.

- **`socialShare()`**  
  - Opens a modal to share to other apps.

- **`presentToast()`**  
  - Presents a toast announcing that message has be successfully copied for 1s

- **`copyText()`**  
  - Copies the wallet address to the clipboard and call `presentToast()` to announce the success.

- **`toFixedDown(value, digit)`**  
  - `value` - the number that will be rounded.  
  - `digit` - the amount of decimal places to be rounded to, only works with whole numbers.  
  - Rounds the `value` to the amount of decimal places specified by the value of `digit` and will always round down the value.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

</details>
&nbsp;

# **Menu**
### The side menu presents a couple of options.  
- `Home` - returns to the **`dashboard`** page.  
- `Send` - opens the page to send currency.  
- `Receive` - opens the page to receive currency.  
- `Transactions` - opens the page to show the transaction history.  
- `NFT Inventory` - opens the page to show the NFT inventory.  
- `Settings` - opens the settings page.
- `Exit Wallet` - logs out of the wallet.

<img src="https://user-images.githubusercontent.com/60563965/185352450-e7d7c0f8-bcb4-4f9c-b5dc-993df4ed5296.png" alt="menu" width="40%">

### **The files for the transactions page will be found in:**  
**`/mobile-web3/src/app/transaction-history`**

- The front end is found in - `/mobile-web3/src/app/transaction-history/transaction-history.page.html`  
- The app logic is found in - `/mobile-web3/src/app/transaction-history/transaction-history.page.ts`  

<details>
    <summary>Code documentation</summary>

Upon initialization, it will call the `setTranslation()` function to set the text to the target language. Save the transaction symbol, list of tokens from an API, url for the tokens and the current cryptocurrency. Call the `getTransaction()` function.
 - API link for token list - <ins>`https://tokens.pancakeswap.finance/pancakeswap-extended.json`</ins>

- **`changeTxType()`**  
  - Returns the token symbol based on the transaction type.

- **`openCalendar()`**  
  - Opens a modal to display a calendar.

- **`presentLoadingCustom()`**  
  - Presents a custom loading screen.

- **`getTransactions()`**  
  - Gets a list of all the past transactions.

- **`getSolTransaction()`**  
  - Gets the most recent 1000 transactions on Solana.

- **`updateTxRange()`**   
  - Displays all the past transactions of the current network.

- **`doInfinite(infiniteScroll)`**  
  - Implements for the infinite scroll in the ionic framework

- **`openBrowser(url)`**  
  - Opens the transaction of the current network in the browser

- **`truncateAddress(str)`**  
  - Checks if the address `str` is longer than 20 characters, if it is, take the 1st 4 characters and the last 4 characters and concatenate them with "..." in between.

- **`copyTxHash(txHash)`**  
  - Copies the transaction hash `txhash` to clipboard and calls `toastMessage()` to announce the success.

- **`toastMessage(data)`**  
  - Presents a toast with the message `data`.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

</details>
&nbsp;

### **The files for the NFT inventory page will be found in:**  
**`/mobile-web3/src/app/nft-inventory`**

- The front end is found in - `/mobile-web3/src/app/nft-inventory/nft-inventory.page.html`  
- The app logic is found in - `/mobile-web3/src/app/nft-inventory/nft-inventory.page.ts` 

<details>
    <summary>Code documentation</summary>

> No code yet

</details>
&nbsp;

### **The files for the settings page will be found in:**  
**`/mobile-web3/src/app/settings`**

- The front end is found in - `/mobile-web3/src/app/settings/settings.page.html`  
- The app logic is found in - `/mobile-web3/src/app/settings/settings.page.ts`  

<details>
    <summary>Code documentation</summary>

Upon initialization, it will call the `setTranslation()` function to set the text to the target language.

- **`copyPrivateKey()`**  
  - Sets the `enterPin` field to be true.

- **`changeLanguage()`**  
  - Opens a modal to change language.

- **`changeCurrency()`**  
  - Opens a modal to change the currency.

- **`handleInput(input)`**  
  - `input` - a string representing the corresponding button clicked.  
  - Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the `pin` field to an empty string, else add `input` to `pin`, if the length of `pin` is 4, presents a loading screen for verifying the pin. Checks if the pin is the same as the pin stored in local storage. If the pin matches, opens the `dashboard` page, else increases the `incorrectPinCounter` field. If the counter is a multiple of 3, block the pin for a set duration of time, else call `presentAlert()` to present the alert. Then closes the loading screen.

- **`presentAlert()`**  
  - Presents an alert showing the amount of attempts remaining before the pin gets blocked.

-  **`presentAlertPinBlocked(duration)`**  
  - Presents an alert showing the amount of time left when the pin has been blocked for multiple incorrect attempts.

- **`doAction(p)`**  
  - Calls a function based on the `component` variable of the parameter `p`.

- **`resetWalletPin()`**  
  - Opens the page to reset the wallet pin.

- **`toastMessage(data)`**  
  - Presents a toast with "data" as the message for 3s.

- **`resentChangeCurrencyLoading()`**  
  - Presents a loading screen for 1s and open the **`dashboard`** page.

- **`toggleRequirePin()`**   
  - Sets the `requirepin` field in the local storage with the `requirePin` field after being stringified.

- **`countDown(duration)`**  
  - Sets the countdown time and updates the time left in the html every 1s.

- **`setTranslation()`**  
  - The function calls the `TranslateService` class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

</details>
