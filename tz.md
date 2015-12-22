# USSD in Tanzania

## Vodacom

### Long codes don't work

In general concatenating multiple steps into long strings *does not* work. For example, the main menu for services other than M-Pesa is at `*149*01#<SEND>`:

![Vodacom TZ main menu](../images/tz/vodacom_main.jpg)

Then choosing option `5<SEND>` (internet) brings up a menu of internet services as expected

![Vodacom TZ internet menu](../images/tz/vodacom_internet.jpg)

However, concatenating into a single long string `*149*01*5#<SEND>` does not display the internet menu. It returns the error:

  > An invalid parameter was entered.

Note that the `01` suffix is required to bring up the menu. `*149#<SEND>` yields the same 'invalid parameter' error above.

### Mobile money flow

Main mobile money menu is at `*150*00#<SEND>`