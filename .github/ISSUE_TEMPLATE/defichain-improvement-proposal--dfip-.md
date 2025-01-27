
<!-- 
As part of the requirement for submission of DFIP for vote of confidence, you are required to pay 50 DFI fee for it to be voted on. After you have submitted this vote of , please transfer 50 DFI to the burn address `8defichainBurnAddressXXXXXXXdRQkSm` and take note of your `txid` and list it here. You may be required to prove that the transfer if yours if there are multiple CFP claims to it. 
Info: https://github.com/DeFiCh/dfips/issues/19

Optionally, you are also encouraged to submit a Reddit discussion thread as part of CFP to allow for a more open discussion with the community. Reddit discussion thread however does not require a fee, you can also use this process to sound out community's acceptance first before committing to it and paying the fee.

Take note that this is a vote of confidence for DFIP, it carries no obligations by the developers to implement the suggestions. DeFiChain is a community projects. Pull requests can be submitted by community and reserved to be evaluated for safety and general community acceptance.
-->

### DFIP Overview
1. Requester(s): Telegram: @Maaze19 & @benbe14
2. Reddit discussion thread (optional): https://www.reddit.com/r/defiblockchain/comments/xd7m6p/dusd_repeg_dfip_discussion_dusd_repeg_by/
3. Proposal fee (50 DFI) txid: c8a92c7713a94066ddba924ea85af5c9a1c926f12cac5fadfbaebd92c9df0993

### Describe your proposal
Simple and intuitive solution to repeg dUSD permanently

Even if dUSD is near to 1$ this DFIP could help avoid bigger depeg trades in the future. 

One sentence summary: take an addtional fee from trades which would unpeg the dUSD-dex-price further and distribute them to those traders, who are helping to repeg dUSD to 1$


Complete Simulation with onchain data (experts): https://1drv.ms/x/s!AjnWQ5JHqJQUcO_izW-NvJyqWAQ?e=86GTKc

### Who has to pay fees?	

Fees have to be paid if a trade is against the oracle price. E.g. if the oracle price of dUSD is 1$, the dex price is 0.90$, selling dUSD will include a fee while buying dUSD will be rewarded with fees collected by sellers. If the dex price is above the oracle price, buyers have to pay a fee while sellers will be rewarded.		

### How will the fee be distributed?					

The collected fee consists of three different parts:
1. Counter trade reward (dynamic)
This part of the fee will be rewarded to the trader who is doing the counter trade (towards peg)

2. Commission (5% of counter trade reward)
The commission will be distributed to liquidity providers as a penalty for the trader to imbalance their position

3. Burn (5% of counter trade reward)
The burn part is an anti whale measure to make it more expensive manipulating prices and help to repeg.


### Which token will be collected as fee?			


If the price is below 1$, fees will be collected and distributed in dUSD, otherwise in DFI.
Because it doesn't make sense to burn USDT or USDC, both have to be automatically converted to DFI when collected (burn part). All other fee parts will be distributed in USDT or USDC.	

### To which pools will the dynamic fee be applied?	

We would like to propose this DFIP only for the dUSD-USDT and the dUSD-USDC Pools. After everything works as planned, this DFIP can be rolled out to dUSD-DFI and all dToken Pairs. Therefore we have to check the impact of delayed oracles due to a long blocktime or stock market data. (New DFIP will follow for this)			

### When would it be activated?	

Because first we have to fill the reward pool, the activation happens in 3 major steps:
1. Implementation
2. Activating through a hard fork
- Commission reward will be paid out
- Burn fee & counter trade reward will be collected until the reward pool is big enough to pay all rewards to repeg price (1$)
3. burn and counter trade rewards activated
- Ensure that never more rewards will be paid out than collected."		


### How will the fee be calculated?			

Fee calculation is simple:
1. check the difference between dex and oracle price BEFORE the swap
2. check the difference between dex and oracle price AFTER the swap
3. Calculate the fee based on data before and after (see playground sheet or example)
4. If the depeg will be bigger, the formula is automatically positive => have to pay
If the depeg will be smaller, the formula is automatically negative => eligible to be rewarded"		

Example:
dUSD < 1$

If a sell of 5000 dUSD would depeg a pool from -5% to -10% fee calculation would look like this:

Caution: free choosen numbers, a sell of 5000 dUSD would never have such a huge price impact (= fee will be way less)

5000*(-5%) = -250 dUSD

5000*(-10%) = -500 dUSD

= |-250 dUSD| + |-500 dUSD| / 20

= 37.5 dUSD counter trade fee

   + 1.875 dUSD (5% burn fee)

   + 1.875 dUSD (5% commission for liq provider)

Sum Fee = 41.25 dUSD (0.825% for 5% further depeg)
				 

### How does this DFIP benefit the DeFiChain community?
1. Potential permanent repeg of dUSD to about $1
2. Benefitting the DefiChain-Ecosystem by helping to repeg dUSD will only give advantages, on the other hand unpeg dUSD or make huge transactions which lead to huge price impacts will be charged with fees
3. burn fee will further help burning dUSD (less algo-dUSD) or DFI which could have a positive longterm impact on the dfi price
4. comission fee will give further rewards for liquidity providers (higher APR)
5. so called "sandwich-bots" will also pay those fees at least on one side of their trades which makes them less profitable and less harmfull

 <!-- Leave the following intact -->
### Non-obligation
I understand that vote of confidence for DFIP carries no obligations by any developers to implement the proposals. DeFiChain is a community projects. Pull requests can be submitted by community and reserved to be evaluated for safety and general community acceptance.
