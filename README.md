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

![System environement](https://imgur.com/a/3tT5blK)

Add the 2 variables into "System variables" where the file path is to the Sdk file in the downloaded Android Studio folder.

![System variables](https://imgur.com/C6gKhn7)

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

```
 npx cap sync android
 npx cap open android 
 *might be wrong
```

The app should be opened in Android Studio where you can run the app on an emulator or on an Android device.

## **To run the app on IOS:**

…

# **Directories**

`/android` - contains the files to allow the app to run on Android devices 

`/e2e` - the end to end folder

`/resources` - folder containing the resources for the app

`/src` - the folder for the source files

`/typings` - 

## **The source code can be found in in the folder:**

> /mobile-web3/src/app













**Change Currency**

## **The files will be found in:**

** /mobile-web3/src/app/change-currency"**

For the modal to change the currency that the value of the token be displayed in.

On initialization gets the "default\_currency" from the local storage and saves it in the "selectedCurrency" field. An array of currencies are also added where each currency is in the form of an array where each contains 2 strings, one for the title and one of the code.

changeCurrency(p)

Changes the "default\_currency" value in the local storage

dismissModal()

Closes the modal

![](RackMultipart20220816-1-h1rdb2_html_92d8e907fdfbe207.png)

**Change Language**

**The files will be found in "**** /mobile-web3/src/app/change-language"**

On initialization an array of languages are added where each language is in the form of an array where each contains 2 strings, one for the title and one of the code.

changeLanguage(p)

Changes the "default\_language" value in the local storage.

dismissModal()

Closes the modal.

![](RackMultipart20220816-1-h1rdb2_html_c283f11aa9b73702.png)

**Change Network**

**The files will be found in "**** /mobile-web3/src/app/change-network"**

Upon construction an array of networks will be added to the "networkList" array, names of each network will be added into the array. The "selectedNetwork" field will be assigned with "current\_network" from the local storage.

On initialization the setTranslation() function is called.

changeNetwork(p)

Assign the name from the parameter "p" to the "selectedNetwork" field. Then the "current\_network" from the local storage is checked with the "selectedNetwork" field, if it is different, then the "selectedNetwork" field will be checked if it's "Solana Mainnet" then a "walletAddress" variable is created and the "SOL\_w\_address" is assigned to the variable from the local storage. If there is no "walletAddress" then the "alertEmptyWalletAdress()" function is called, else variables from the local storage will be changed and variables will be removed from the storage. If it is not "Solana Mainnet" the same set of processes will be repeated with "BSC Mainnet", "Ethereum Mainnet" and "Polygon Mainnet".

dismissModal()

Closes the modal.

alertEmptyWalletAdress()

Creates an alert with header, subheader, and messages based on the fields. Also contains 3 buttons, one button for creating a wallet that redirects to the "mnemonic" page with the role of 'ok', one button to import a wallet that redirects to the "import-wallet" page with the role of 'ok' and one button to cancel and assigns the "currentNetwork" field to the "selectedNetwork".

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

![](RackMultipart20220816-1-h1rdb2_html_9aea0142a07c5f23.png)

**Dashboard**

**The files will be found in "**** /mobile-web3/src/app/dashboard"**

A tab in the tabs page.

Upon initialization, it will call the "setTranslation()" function, as well as set the "walletAddress" field to "w\_address" field from the local storage. The "coins" field will also be assigned with an empty array. The "current\_network" field from the local storage will be checked to see which mainnet it's set to and the relevant value will be assigned to the "currentTokenListToUse" field.

The token list to use to be taken from the local storage and parsed and will be assigned to the variable "tokenArray". A check will be run to check if "tokenArray" is null, if it's not, an array will be made from "tokenArray" and assigned to the field "coins".

The "allTokenList" and "allIconList" fields are assigned with empty arrays. The icon for the network is taken from the local storage, parsed and assigned to the "iconList" variable. A check will be run to check if "iconList" is null, if it's not, an array will be made from "iconList" and assigned to the field "allIconList".

The "truncateAddress() function will be run with the "walletAddress" field as the parameter and the return value will be assigned to the "shownWalletAddress" field.

The "updateETHPrice()" and "getGlobalTokenList()" functions will be run.

changeNetwork()

Creates a modal for changing networks and presents the modal. Get the "current\_network" field from the local storage and assign it to the "oldNetwork" variable. The "oldNetwork" field will be checked with the "current\_network" after any changes and if it's not the same, relevant fields about tokens in the local storage will either be set as an empty string or as 0. Then the dashboard page will be loaded back.

changeAccount()

Opens a modal that provides the changing account service.

copyAddr()

Copies the contents of the "walletAddress" field to the clipboard, then calls the "toastMessage()" function with the "successCopyMessage" field as the parameter.

addAccount()

Calls the "alertAddAccount()" function.

mainPushSendPage()

Opens the send-transaction page.

pushReceivePage(symbol, balance)

Opens the receive-transaction page, with the parameters as extras for the navigation.

pushSendPage(symbol, balance, address, usd)

Opens the send-transaction page, with the parameters as extras for the navigation.

doRefresh(refresher)

Calls the refresher and calls the "updateETHPrice()" and "getGlobalTokenList()" functions and completes the refreshing process.

truncateString(str, num)

str - the string to be truncated

num - number of characters to be truncated

The function truncates the given string (str) leaving only the first "num" amount of characters and leaving "..." after. If the given string is shorter or the same length than the amount of characters of "num" the string will be returned as it is.

truncateAddress(str)

Checks if the address (str) is longer than 20 characters, if it is, take the 1st 4 characters and the last 4 characters and concatenate them with "..." in between.

toFixedDown(value, digit)

value - the number that will be rounded

digit - the amount of decimal places to be rounded to, only works with whole numbers.

Rounds the "value" to the amount of decimal places specified by the value of "digit" and will always round down the value.

toastMessage(data)

data - a string that will be presented in the toast

A toast will be created and will last for 1 seconds and present "data" as the message.

getETHBalance()

Checks if the "currentNetwork" field is "Solana Mainnet" if it is, gets the balance using the wallet address from "walletAddress". The "tmp" variable is then created and will be assigned the balance divided by "LAMPORTS\_PER\_SOL", and the "balanced\_ETH" field from the local storage will be set with "tmp" after it gets stringfied.

If the current network is not Solana Mainnet, the "tmpAddress" variable will be created and be assigned with "w\_address" from the local storage. The "balance\_ETH" field will be assigned with the balance.

After setting "balance\_ETH" in the local storage for both the if and else case, the "balance\_ETH" field will be assigned with the same field from the local storage and the "value\_ETH" field will be assigned with the number of "balance\_ETH" multiplied with the number of "price\_ETH", and if "value\_ETH" is not a number it will be set to 0.

updateETHPrice()

Updates the price of ETH in the current selected currency.

getGlobalTokenList()

Check if the "currentNetwork" field is "BSC Mainnet" if it is, set the "currentTokenListToUse" field to "myTokenBSC". Then try calling the api. If the "tokens" array in the api has a length more than 0, assign an empty array to the "allTokenList" field. Then loop through the "tokens" array, adding each entry into the "allTokenList" array. Then call the "removeExistingToken() and "removeExistingFavouriteToken()" functions with the "coins" field as the parameter, and set the "allTokensBSC" field in the storage with the "allTokenList" field as a string.

If an error happens, a variable "allTokens" will be assigned with the "allTokensBSC" field from the storage after being parsed, and if "allTokens" is not null, and array will be formed from "allTokens" and assigned to the "allTokenList" field.

Then try to call the api for getting the token of the given wallet address. If the length of the "coins" array in the api is more than or equal to 0, call the "tidyTokenInfo()" function with the "data.items" from the api as the parameter.

If the "currentNetwork" field is not "BSC Mainnet", repeat the process for "Solana Mainnet".

removeExistingToken(tokenList)

tokenList - an array of tokens

Removes the tokens from the "allTokenList" array that matches an entry in "tokenList".

removeExistingFavouriteToken(tokenList)

tokenList - an array of tokens

Removes the favorite tokens from the "allFavouriteTokenList" array that matches an entry in "tokenList".

tidyTokenInfo(tokenList)

tokenList - an array of tokens

Loops through "tokenList" and checks if the current network in the "currentNetwork" field matches the corresponding token in the "contract\_name" field of "tokenList", if it is skip to the next iteration, else set the relevant fields about the tokens in the local storage and storage.

getDataUri(targetUrl, tokenSymbol)

targetUrl - the url to get the file

tokenSymbol - the filename without the extension

Gets the file from the target url and returns the downloaded file, if an error occurs, it will be logged to the console.

delay(ms)

Adds a delay for "ms" amount of milliseconds.

alertAddAccount()

Creates an alert for adding an account, creating an account and closing the alert.

createNewAccount()

Sets the "accountList" field to an empty array. Checks if the current network is either BSC, ETH or MATIC Mainnets, if yes, change the relevant account information in the local storage and as well as change the "derivationPath" field. If the current network is Solana Mainnet, change the "derivationPath" field.

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

**Home**

**The files will be found in "**** /mobile-web3/src/app/home"**

Upon initialization, it will initialize the web3 functions.

Upon construction it set the default network and the default currency in the local storage and set the array of languages used in the "languages" field.

pushWelcome()

Opens the welcome page.

changeLanguage()

Translates and set as default language based on "defaultLanguage" field.

**Import Wallet**

**The files will be found in "**** /mobile-web3/src/app/import-wallet"**

Upon initialization, it will call the "arrangeMnemonic()" function with an empty string, and on construction it will set up the array of networks in the "networks" field and call the "setTranslation()" function.

handleInput(input)

input - a string representing the corresponding button clicked

Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the "pin" field to an empty string, else add "input" to "pin", if the length of "pin" is 4, delay for 0.1s and sets "verifyPin" field to true to verify the pin.

handleConfirmInput(input)

input - a string representing the corresponding button clicked

Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the "pin" field to an empty string, else add "input" to "confirmPin", if the length of "confirmPin" is 4, delay for 0.1s and checks if "confirmPin" is same as "pin", if it is sets "createPin" and "verifyPin" fields to false and finish, else calls "presentAlert()", set "verifyPin" to false, and "confirmPin" and "pin" to an empty string and finish. `

doContinue()

Submits the mnemonic and checks if the submitted mnemonic is valid.

submitPKey()

Checks if the network used is Solana Network, if it is use to private key from "myPrivateKey" field to login to Solana with necessary information, else use the private key from "myPrivateKey" to log into Ethereum with the necessary information.

arrangeMnemonic()

Arranges the list of mnemonics in a grid of 3 columns.

pasteMnemonic()

Pastes the contents of the clipboard in the form of a space-delimited list to "list\_mnemonic" and arrange the mnemonic with the "arrangeMnemonic()" function.

switchValue(value)

value - a number

Assigns the "value" parameter to the "value\_selected" field and call the "arrangeMnemonic()" function with an empty string as parameter.

importPKey(ev)

Assigns the "myPrivateKey" field with the "ev" parameter.

getAddress(mnemonic)

Gets the address of the wallet using the mnemonic input as the parameter and is stored in the local storage and storing the encryption keys in the storage.

presentAlert()

Presents an alert to inform the user the pin for confirmation doesn't match.

presentAlert2()

Presents an alert to inform the user the pin inputted is invalid and they have to try again.

presentAlert2FA()

Presents an alert, has 2 buttons, one for yes and opens the "two-factor-authentication" page, and one for no which saves the wallet information in local storage and opens the "dashboard" page.

changeNetwork()

Changes the "isSolanaNetwork" to the opposite of the current value.

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

**Mnemonic**

**The files will be found in "**** /mobile-web3/src/app/mnemonic"**

On initialization calls the "generateMnemonic()" function, and on construction sets the translation of the text and sets the derivation paths in the local storage. If there is a pin in the storage, get the wallet path from the local storage and store in the relevant fields, and set the current network in the field.

generateMnemonic()

Sets the "strength" variable based on the value of "value\_selected" field. Generates a mnemonic with the "generateMnemonic()" function from bip39 using a word list and the "strength" variable and assign to the "mnemonic" field. Use split the mnemonic into an array and use to to call the "arrangeMnemonic()" function.

copyMnemonic()

Copies the mnemonic stored in the field to the clipboard and calls the "toastMessage()" function to display a success message as a toast.

arrangeMnemonic()

Arranges the list of mnemonics in a grid of 3 columns.

getAddress(mnemonic)

Gets the address of the wallet using the mnemonic input as the parameter and is stored in the local storage and storing the encryption keys in the storage.

handleInput(input)

input - a string representing the corresponding button clicked

Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the "pin" field to an empty string, else add "input" to "pin", if the length of "pin" is 4, delay for 0.1s and sets "verifyPin" field to true to verify the pin.

handleConfirmInput(input)

input - a string representing the corresponding button clicked

Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the "pin" field to an empty string, else add "input" to "confirmPin", if the length of "confirmPin" is 4, delay for 0.1s and checks if "confirmPin" is same as "pin", if it is sets "createPin" and "verifyPin" fields to false and finish, else calls "presentAlert()", set "verifyPin" to false, and "confirmPin" and "pin" to an empty string and finish.

presentAlert()

Presents an alert to inform the user the pin for confirmation doesn't match.

presentAlert2FA()

Presents an alert, has 2 buttons, one for yes and opens the "two-factor-authentication" page, and one for no which saves the wallet information in local storage and opens the "dashboard" page.

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

**Pin**

**The files will be found in "**** /mobile-web3/src/app/pin"**

Upon initialization, call the "checkCountDown()" function.

pushResetPinPage()

Opens the "reset-wallet-pin" page.

handleInput(input)

input - a string representing the corresponding button clicked

Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the "pin" field to an empty string, else add "input" to "pin", if the length of "pin" is 4, checks if the pin is the same as the pin stored in local storage. If the pin matches, opens the "dashboard" page, else increases the "incorrectPinCounter" field. If the counter is a multiple of 3, block the pin for a set duration of time, else call "presentAlert()" to present the alert.

countDown(duration)

Sets the countdown time and updates the time left in the html every 1s.

presentAlertPinBlocked(duration)

Presents an alert showing the amount of time left when the pin has been blocked for multiple incorrect attempts.

presentAlert()

Presents and alert showing the amount of attempts remaining before the pin gets blocked.

checkCountDown()

Check if the count down timer has finished.

Get the time when the countdown ends and set it as a variable "endTime", and set the current time to the variable "now". The variable "distance" will be the difference between "endTime" and "now". If "now" is before "endTime" , call the "countDown()" function with "distance" to set the remaining time left. If "now" is the same or after "endTime" the countdown timer will stop showing.

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

**Receive Transaction**

**The files will be found in "**** /mobile-web3/src/app/receive-transaction"**

Upon initialization, it will call the "setTranslation()" function to set the text to the target language. Sets the "t\_symbol" field to the corresponding network if it's Ethereum, BSC or Polygon, else it will be left as undefined. Set the "t\_balance" field to the balance stored in the local storage, if there's no balance, leave "t\_balace" as undefined.

socialShare()

Opens a modal to share to other apps.

presentToast()

Presents a toast announcing that message has be successfully copied for 1s

copyText()

Copies the wallet address to the clipboard and call "presentToast()" to announce the success.

toFixedDown(value, digit)

value - the number that will be rounded

digit - the amount of decimal places to be rounded to, only works with whole numbers.

Rounds the "value" to the amount of decimal places specified by the value of "digit" and will always round down the value.

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

**Send Transaction**

**The files will be found in "**** /mobile-web3/src/app/send-transaction"**

Upon initialization, it will call the "setTranslation()" function to set the text to the target language. Import information from the local storage to the field. Call the "checkCountDown()" function to check if the countdown is over. If the current network is not Solana, call the "getGasFeeEstimate()" function to get an estimate of the gas fee, else get the private key for solana from the local storage and store it in the "solanaPrivKey" field.

getGasFeeEstimate()

Check if the network is BSC, if yes, call the api to get the gas fee for "fast", "average" and "slow". If the network is Solana…

checkCountDown()

Check if the count down timer has finished.

Get the time when the countdown ends and set it as a variable "endTime", and set the current time to the variable "now". The variable "distance" will be the difference between "endTime" and "now". If "now" is before "endTime" , call the "countDown()" function with "distance" to set the remaining time left. If "now" is the same or after "endTime" the countdown timer will stop showing.

scanQR()

Uses the barcode scanner plugin and opens the camera to scan a QR code. Check the address of the QR code, and finish scanning.

sendAllBalance()

Sends the payment as long as the current value is less than or equals to the balance.

countDown(duration)

Sets the countdown time and updates the time left in the html every 1s.

handleInput(input)

input - a string representing the corresponding button clicked

Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the "pin" field to an empty string, else add "input" to "pin", if the length of "pin" is 4, presents a loading screen for verifying the pin. Checks if the pin is the same as the pin stored in local storage. If the pin matches, opens the "dashboard" page, else increases the "incorrectPinCounter" field. If the counter is a multiple of 3, block the pin for a set duration of time, else call "presentAlert()" to present the alert. Then closes the loading screen.

presentAlertPinBlocked(duration)

Presents an alert showing the amount of time left when the pin has been blocked for multiple incorrect attempts.

presentAlert()

Presents an alert showing the amount of attempts remaining before the pin gets blocked.

presentNoTokenAccountAlert()

Presents an alert informing the user that there is no token account and gives the option to create a token account or cancel.

presentsCreatedTokenAccountAlert()

Alerts after a token account is created and has the option of creating a transaction.

checkAddress(ev)

Checks the validity of the given address "ev".

updateAmountToSend(ev)

Checks if the amount is enough to be sent, if the current amount is less than the balance, call the "updateValue()" function with the amount to send and set the "insufficientBalance" field to false, else set the "insufficientBalance" field to true.

updateValue(tokenAmount)

tokenAmount - the amount of tokens

Updates the value of the token in USD.

toFixedDown(value, digit)

value - the number that will be rounded

digit - the amount of decimal places to be rounded to, only works with whole numbers.

Rounds the "value" to the amount of decimal places specified by the value of "digit" and will always round down the value.

openBrowser(transactionHash)

Opens a browser with the corresponding network that the transaction was done in to display the transaction.

shareReceipt()

Captures a screenshot and opens a modal to allow sharing the screenshot to other apps.

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

backToRoot()

Changes to the "dashboard" page.

toConfirmSend()

Sets the "enterPin" field to be true.

createTransaction()

Opens a loading screen and process the amount that will be sent.

createTokenAccount()

Opens a loading screen and process the creation of the token account.

sendTransaction()

Opens a loading screen and process the tokens to be sent.

toBaseUnit(value, decimals, BN)

Converts a number into a big number.

presentAlertTransactionFailed()

Presents an alert informing the failure in the transaction. Has a button with the 'ok' role that calls the "backToRoot()" function to return to the "dashboard" page.

**Settings**

**The files will be found in "**** /mobile-web3/src/app/settings"**

Upon initialization, it will call the "setTranslation()" function to set the text to the target language.

copyPrivateKey()

Sets the "enterPin" field to be true.

changeLanguage()

Opens a modal to change language.

changeCurrency()

Opens a modal to change the currency.

handleInput(input)

input - a string representing the corresponding button clicked

Handles the input from the keypad for creating the pin, first checks if the button pressed is clear, if it is sets the "pin" field to an empty string, else add "input" to "pin", if the length of "pin" is 4, presents a loading screen for verifying the pin. Checks if the pin is the same as the pin stored in local storage. If the pin matches, opens the "dashboard" page, else increases the "incorrectPinCounter" field. If the counter is a multiple of 3, block the pin for a set duration of time, else call "presentAlert()" to present the alert. Then closes the loading screen.

presentAlert()

Presents an alert showing the amount of attempts remaining before the pin gets blocked.

presentAlertPinBlocked(duration)

Presents an alert showing the amount of time left when the pin has been blocked for multiple incorrect attempts.

doAction(p)

Calls a function based on the "component" variable of the parameter "p".

resetWalletPin()

Opens the page to reset the wallet pin.

toastMessage(data)

Presents a toast with "data" as the message for 3s.

presentChangeCurrencyLoading()

Presents a loading screen for 1s and open the "dashboard" page.

toggleRequirePin()

Sets the "requirepin" field in the local storage with the "requirePin" field after being stringified.

countDown(duration)

Sets the countdown time and updates the time left in the html every 1s.

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

**Transaction History**

**The files will be found in "**** /mobile-web3/src/app/transaction-history"**

Upon initialization, it will call the "setTranslation()" function to set the text to the target language. Save the transaction symbol, list of tokens, url for the tokens and the current cryptocurrency. Call the "getTransaction()" function.

changeTxType()

Returns the token symbol based on the transaction type.

openCalendar()

Opens a modal to display a calendar.

presentLoadingCustom()

Presents a custom loading screen.

getTransactions()

Gets a list of all the past transactions.

getSolTransaction()

Gets the most recent 1000 transactions on Solana.

updateTxRange()

Displays all the past transactions of the current network.

doInfinite(infiniteScroll)

Implements for the infinite scroll in the ionic framework

openBrowser(url)

Opens the transaction of the current network in the browser

truncateAddress(str)

Checks if the address (str) is longer than 20 characters, if it is, take the 1st 4 characters and the last 4 characters and concatenate them with "..." in between.

copyTxHash(txHash)

Copies the transaction hash "txhash" to clipboard and calls "toastMessage()" to announce the success.

toastMessage(data)

Presents a toast with the message "data".

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

**Two Factor Authentication**

**The files will be found in "**** /mobile-web3/src/app/two-factor-authentication"**

Upon initialization, it will call the "setTranslation()" function to set the text to the target language, and call "getTwoFactorAuthenticationCode()".

getTwoFactorAuthenticationCode()

Generate a password and save it to the variable "secretCode". Encodes "secretCode" into base32 and stores the code into "mfaSecret" field. Stores the url of the password in "mfaUrl"

Use "mfUrl" to generate a QR code and store in the "qrcode" variable then store in the "mfaQR" field.

checkTwoFactorAuthenticationCode(userToken)

Verifies the user token to the code "mfaSecret".

copyKey()

Copies the key from "mfsSecret" field to clipboard and calls "toastMessage()" to announce it was successful.

toastMessage(data)

Presents "data" as the message of a toast for 1s.

presentSuccessfulAlert()

Presents an alert to alert the success of the verification, and stores the key to the storage and other information local storage, then opens the dashboard page.

presentSuccessfulAlert2()

Presents an alert to alert the success of the verification, and stores the key to the storage, then opens the dashboard page.

setTranslation()

The function calls the "TranslateService" class to get text for each given parameter translated to the target language and the text will be assigned to the field that corresponds to the text.

**Welcome**

**The files will be found in "**** /mobile-web3/src/app/welcome"**

Upon construction, check if there's a wallet, if yes, open the tabs page, else set the "showPage" field to true.

pushImportPage()

Opens the import wallet page to import a wallet.

pushCreateWalletPage()

Opens the mnemonic page to create a wallet.
