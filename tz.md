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

The send money flow, shows similar behavior except that instead of an error, any code beginning with `*150*00*` yields the main mobile money menu. 