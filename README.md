# Pancakeswap v2 trading client
A Pancakeswap trading client (and bot) with limit orders, stop-loss, custom gas strategies, a GUI and much more.

![alt text](https://raw.githubusercontent.com/aviddot/Pancakeswap-trading-bot/main/v1gif.gif "GIF application")

<H2>Prerequisites</H2>

- An ethereum/bsc address
- A Windows machine
- <i>Not sure whether needed anymore: Visual C++ build tools (www.visualstudio.microsoft.com/visual-cpp-build-tools/)</i>

<br> </br>
<H2>Getting started</H2>

0. Read prerequisites

1. Download the latest release or download "configfile.py" and "pancakeswap_bot.exe" from the repository.


2. Open "configfile.py" (with notepad for instance) and add your ethereum address and personal key at the bottom of the file between the quotation marks('').

<pre>...
my_address = ''
my_pk = ''</pre>


3. Run "pancakeswap_bot.exe"

- Make sure configfile.py and bot.exe are in the same folder.


5. Edit settings according to choice.


<br> </br>
<H2>Functions</H2>


<b>Main coin/token</b>: The token or coin you want to trade tokens for and with

<b>Buy/Sell boundary</b>: The amount of balance (calculated in $) that has to be present in (main-)tokens or coins has to be present in the wallet, to deduct whether the latest action was a buy or a sell. For instance: if the value is 100, your maincoin option BNB and have 120$ worth of BNB on your address, the bot will see the latest action as "sell".

<b>Token address</b>: Fill the token address of the token you want to trade (such as 0x0000000000000000000000000000000000000000)

<b>Token name</b>: The name of the token, fill it in yourself

<b>Dec.</b>: The amount of decimals the token operates with (18 is normal)

<b>Sell($)</b>: The price you want the trader to sell the token for (0.01 = 1 dollar cent)

<b>Buy($)</b>: The price you want the trader to buy the token for (0.01 = 1 dollar cent)

<b>Activate and Trade with BNB</b>: Toggle if you want to activate trading with your main-coin/token

<b>Trade with BEP (Experimental!)</b>: Toggle if you want to trade the token with other BEP20 tokens of which this option is activated (see tokentokennumerator)

<b>Stoploss</b>: Toggle to activate stoploss (0.01 = 1 dollar cent)


<b>Second(s) between checking price</b>: Standard is 4 seconds. With a infura server with max 100.000tx/day 4 seconds is good for 2 activated token 24hr/day


<b>Seconds waiting between trades</b>: depends on how fast transactions finalize
<b>Max slippage</b>: The maximum slippage you want to allow while trading (0.03 = 3%)
<b>$ to keep in ETH after trade</b>: The amount of ETH/main token you want to keep after each trade (excluding transaction fees) in terms of $.
<b>GWEI</b>: The amount of gas you want to use for each trade (5 GWEI is fine)


<b>Different deposit address</b>: Use this if you want the swap output to go to a different ethereum address (without extra fees).

<b>Tokentokennumerator (Experimental!)</b>: This value lets you trade ERC tokens with each other. The code to create the value is as followed:

<pre>if pricetoken1usd > ((token1high + token1low) / 2) and pricetoken2usd < ((token2high + token2low) / 2):
  token1totoken2 = ((pricetoken1usd - token1low) / (token1high - token1low)) / ((pricetoken2usd - token2low) / (token2high - token2low))</pre>
  
  If you dont want to wait till the token1 is sold for the maincoinoption, because you are uncertain whether token2 will still be at this price level or think that token1 will     drop, you can use this function. To use this function, "Trade with ERC" should be activated for at least 2 tokens, and the highs and lows should be set seriously.
    
  As an example, if the current price of token1 is $0.9 and its set "high"=$1 and "low"=$0, the value of this token is seen as "90%". Token2 also has a high of $1, but the         current price is 0.2$, value of this token is seen as 20%. The tokentokenmnumerator is set at 3.3. If we divide the 90% by the 20%, we get 4.5, which is higher than 3.3, which   means that token1 gets traded for token2 instantly. If the tokentokennumerator was set to 5, the swap would not happen.
  
<br> </br>
<H2>Changelog v1</h2>

- Recoded my uniswap bot to work with pancakeswap. This project was also made to fix bugs in the uniswap-bot, because the transaction fee's are so low.

<br> </br>
<H2>Current bugs</h2>


- Some tokens or trading amounts are not possible to trade with, due to this issue: https://github.com/ethereum/web3.py/issues/1634
  This is the error-message you get: "Python int too large to convert to C ssize_".
  If you get this error its best to exclude the token (which probably has a very low price per token) or trade with lower amounts.
- Sloppy dinamic design of GUI
- Sometimes lag when updating names or when starting the bot (0-10 seconds)
- More: Let me know!

<br> </br>
<H2>To do</H2>

- Let the amount of decimals and the token-name be derived automatically (like in the uniswap-bot)
- New, more user-friendly design
- Fix "Python int too large to convert to C ssize_"

(Depends on whether the application is used)

<br> </br>
<H2>Author</H2>

If you have any questions you can contact me via telegram: aviddot
<br> </br>
Donations: 0x6B1CeA1c27Bbb1428978dC3C0423642fDa404367



<br> </br>
<H2>Disclosure</H2>
I own some of the tokens portayed in the gif. These tokens are used only for example purposes and are not meant to be an endorsement. I am not affiliated with these tokens or any subsidiaries. Use the application at your own risk, I am not in any way responsible for losses.

  

