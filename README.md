# CrypFinder Bot 
## Version 1.2

## CrypFinder Summary: 
CrypFinder is a Coinbase Pro API trading bot that currently implements a basic momentum trading strategy in NodeJS using the Coinbase Pro API, as well as its own custom library for the endpoints that are not supported by the now deprecated Coinbase Pro NodeJS Library. Currently, Coinbase Pro limits the number of portfolios to five, this means that the bot can run up to four trading instances simultaneously per Coinbase Pro account. This bot can be modified to trade any product pairs available on Coinbase Pro, such as BTC-USD, ETH-USD, etc., but stablecoin and crypto markets haven't been tested yet, only USD markets. 

The currently implemented momentum strategy will work as follows: The bot will start by getting the amount of USD available for the provided API key's profile. If the amount is greater than zero, it will monitor the price changes of the chosen product using a peak/valley system; if the price changes by the specified delta, it will purchase a position. Then, it will monitor price changes until the delta condition and profit condition are met; after selling for a profit, it can deposit a cut of the profit to a different portfolio for saving. 

The bot features a number of variables at the top that can be configured to customize how it trades. This includes the deltas that specify an amount of price change that will trigger a buy/sell, the name of currency to trade, the profile names, the deposit enable/disable flag, the deposit amount, and more. Of course, any of the code can be modified to customize it fully. This project is a great way to trade crypto on Coinbase Pro through their API. It also could make a good starting point to design your own crypto trading algorithm.

## How to run the program:
I suggest starting by using this program in the [Coinbase Pro Sandbox](https://docs.pro.coinbase.com/#sandbox) for testing. 
1. Create a coinbase pro account. Install NodeJS, install Git, consider adding an ESLint plugin to your IDE to use the eslint configuration.
2. Setup your Coinbase Pro account portfolios (profiles), this is an important part of the bot. The bot will swoop up any available balance in a profile and start trading with it, so in order to safely store some of the profits you must specify another profile to deposit to. Currently, Coinbase Pro limits profiles to five. I recommend setting up the portfolios with the Default, Profit savings, and ___ trader (I.E. 'BTC trader' if it's trading BTC) for the other available three slots. Don't trade in the default profile because if you transfer money in, it could get swept up by the bot before you can allocate it where you want to. Alternatively, you could deposit profits in the default portfolio; this would open up four profiles for bot trading. 
3. Create the API key for the profile you want the bot to trade on, give it View/Trade/Transfer permissions and whitelist your public IP. [More info here](https://help.coinbase.com/en/pro/other-topics/api/how-do-i-create-an-api-key-for-coinbase-pro). 
4. Clone the github repo locally and run `npm install` from within the repo directory.
5. Configure the variables at the top of index.js to select your environment, Deltas, fee amounts, product to trade, and profile names.
6. Create a .env file in the root directory of the projects repo with the following:

    API_KEY=\<your API key>

    API_SECRET=\<your API secret>

    API_PASSPHRASE=\<your API passphrase>

    Additionally consider adding `LOG_LEVEL=debug` here if you want the full debug logs.

7. Add some funds to your default portfolio and make sure there is no existing coin balance for the product you're trading.
8. Run the program with `node index.js` from within the repo directory.

## How to contribute:
1. Fork the repo.
2. Clone the github repo locally and run `npm install` 
3. Switch to the latest development branch to get the up-to-date progress.
4. Create a new branch with a name that describes the feature/change you're making.
5. Check the roadmap for ideas of things to work on.
6. Make your changes and commit them with a descriptive message.
7. Push your changes upstream.
8. When you're done testing your changes, create a PR in your forked repository. Select LeviathanLevi/Coinbase-Pro-Crypto-Trading-Bot-CrypFinder to merge into. Then wait for approval.

## Running the program out of sandbox:
When you're confident in the configuration/code base and want to run it in the real environment, comment out the sandbox env variables and uncomment out the real API URI variables. Update the .env file with a valid API key. You can run this program on your own machine or consider using a server such as an AWS EC2 instance with an EIP (you need to whitelist the API IP). AWS EC2 offers a free tier instance for a year that works well for hosting.

## Helpful links:
[Coinbase Pro](https://pro.coinbase.com/trade/BTC-USD)

[Coinbase Pro API Docs](https://docs.pro.coinbase.com/#introduction)

[Coinbase Pro NodeJS Library](https://www.npmjs.com/package/coinbase-pro)

[Flow diagram of the momentum strategy, open it in Google draw.io for best results (May be outdated, but can help to give an idea of how the program works)](https://drive.google.com/file/d/1sMg7nWcuCDwHS5wdwHgoe5qqODO7UEFA/view?usp=sharing)

## Roadmap: 
- Test trading on stable coin market and implement any fixes needed to make it work.
- Test trading on crypto markets and implement any fixes needed to make it work.
- Implement a CLI (command line interface) to control the bot.

### Possible future goals:
- Add more strategies or make the current momentum strategy better.
- Implement a way to run the bot against historical data to test performance.

## Interested in the project?:
Consider getting involved. Free to contact the creator on GitHub ([Levi Leuthold](https://github.com/LeviathanLevi)) for information on how to get started! Checkout the product roadmap to see what features are needed/planned for the future or add your own ideas. 

## Contributors:
Levi Leuthold - Creator