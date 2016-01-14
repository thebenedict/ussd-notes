# USSD in Tanzania

## Vodacom

### Send money flow

M-Pesa send money via USSD with a reply over SMS. The flow starts from the main mobile money menu at `*150*00#<SEND>`:

![Vodacom send money step 1 of 7](/images/tz/vodacom_send_money_1of7.jpg?raw=true)
![Vodacom send money step 2 of 7](/images/tz/vodacom_send_money_2of7.jpg?raw=true)
![Vodacom send money step 3 of 7](/images/tz/vodacom_send_money_3of7.jpg?raw=true)
![Vodacom send money step 4 of 7](/images/tz/vodacom_send_money_4of7.jpg?raw=true)
![Vodacom send money step 5 of 7](/images/tz/vodacom_send_money_5of7.jpg?raw=true)
![Vodacom send money step 6 of 7](/images/tz/vodacom_send_money_6of7.jpg?raw=true)

Response via SMS:

![Vodacom send money step 7 of 7](/images/tz/vodacom_send_money_7of7.jpg?raw=true)

### Long codes don't work

In general concatenating multiple steps into long strings *does not* work. For example, the main menu for services other than M-Pesa is at `*149*01#<SEND>`:

![Vodacom TZ main menu](/images/tz/vodacom_main.jpg?raw=true)

Then choosing option `5<SEND>` (internet) brings up a menu of internet services as expected:

![Vodacom TZ internet menu](/images/tz/vodacom_internet.jpg?raw=true)

However, concatenating into a single long string `*149*01*5#<SEND>` does not display the internet menu. It returns the error:

  > An invalid parameter was entered.

Note that `*149#<SEND>` yields the same 'invalid parameter' error, i.e. the `01` suffix is required to bring up the menu.

The send money flow shows similar behavior except that instead of an error any code beginning with `*150*00*` yields the main mobile money menu.

It's surprisingly hard to google more information on this, and why it works on some networks and not others. [This site](http://andreicostin.com/index.php/brain/2010/01/06/learning_gsm_ussd_fuzzing_and_attacking_) has a discussion of long codes being limited by operators because they're used to execute some simple types of fraud:

 > The idea was simple and useful (if implemented correctly :) ). Some subscriber could transfer some credit (between let’s say 1 EUR and 20 EUR) to another pre-pay subscriber of the same network. This was implemented as USSD menu in steps. However, the same thing could be accomplished by sending the entire menu-path and application parameters/configuration (like amount of credit, destination number, final confirmation of transfer, etc.) as one short-cut USSD string (example: *123*4*9*7*0745123456*1#, where 123 is self service USSD application, 4->9 is the menu path for credit transfer, 7 is the amount of 7 EUR, 0745123456 is the destination subscriber number, 1 is YES as final confirmation).

 > Soon, a HUGE amount of mail/messenger/sms spam was flying around saying roughly:

 > “A former GSM technical employee was fired and he open a secret code as a revenge on GSM employer. The code let’s you top-up your account with unlimited calls. Just type *123*4*9*20*0745666666*1# and send on you phone and the code will be activated".

 > Here the scam was that the spammer’s number was 0745666666 and he was actually getting 20 EUR from the victim’s account (if the credit was there of course :) - that’s why a thoughtful scammer would choose a very probable to exist in victim’s account lower credit like 4 EUR or 5 EUR).

 > Lot’s of stupid-and-greedy people were caught on losing their own money. The scammers got a lot of credit. They can trade for real-money in a proportion of 1-to-2 let’s say. They can trade it using the same buggy USSD credit transfer application that got them the credit in the first place :) or just use the credit for calls. Also, the pre-pay cards are anonymous, so you don’t have an identity linked directly to it, so the complaints to authorities and to TELCOs by the victims have no way to punish the abusers.

 > So, the lesson was somehow learned and the TELCOs now offer the credit transfer application via step-by-step menu navigation - no more one shortcut USSD string.


## Tigo

### Send money

`*150*01#`

`1` (Send Money)

`1` (To Mobile Number)

[ENTER RECIPIENT NUMBER]

[ENTER AMOUNT]

[ENTER PIN]

### Check balance (costs TSH 50)

`*150*01#`

`5` (My Account and Balances)

`2` (Check Balance)

[ENTER PIN]
