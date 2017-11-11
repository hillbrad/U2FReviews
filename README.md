# U2FReviews

Reviews of U2F devices

Adam Langley got the ball rolling with his reviews [here](https://www.imperialviolet.org/2017/08/13/securitykeys.html), much of the content of which is reproduced here with his permission.  I've used a number of U2F devices Adam hasn't, and played around with NFC and Bluetooth Low Energy (BLE) connectivity, as well as multifunction devices, so at the request of some friends here's an expanded set of reviews.  It's set up as a GitHub repo and I encourage you to submit PRs with reviews of devices you've used that aren't listed here. *-Brad*

-------

Update: AGL has published some further test results for his series of U2F devices here: https://www.imperialviolet.org/2017/10/08/securitykeytest.html  

He notes a number of implementation flaws or deviations from the standard. Mostly these are inconsequential to the ordinary use of the devices, but the KEY-ID and HyperFIDO devices have flaws that could allow a site to identify two different accounts at their service using the same hardware device, something which shouldn't be possible according to the FIDO specifications.

-------

## Google Advanced Protection:

Google recently launched an advanced account security program. https://landing.google.com/advancedprotection/ It hardens your account against phishing and account recovery attacks and requires a U2F confirmation for every login.  You must register two security keys to enable this feature, and number of people have asked me which I recommend, or more simply, which ones work. I recommend the following:

### For Android Users:

Yubikey NEO + a second Yubikey NEO or a Yubikey 4C or 4C Nano if you want a USB-C device. 

NFC has superior usability to BLE for mobile uses, doesn't need a batery and thus the devices can be more robust.  The TOTP features also available on the NEO or 4-series Yubikeys are a great addition, but you should have two devices that can do this, and save each seed to both in case one fails.  

Unfortunately, you can't yet use an NFC-only device like the Fidesmo card because Google still only supports registering a new device over USB. The Feitian MultiPass works, but I don't recommend it because the NFC antenna is so bad.

### For iOS Users:

Yubico U2F Security Key + VASCO DigiPass SecureClick

On iOS, you have to use BLE with the Google Smart Lock app to login.  The only device I've found that works with this is the VASCO DigiPass SecureClick.  The Feitian MultiPass should work in theory, and I've heard from people that got it to work, but I've tried to pair my MultiPass to three different iOS devices with no success.

As a backup, the Yubico U2F only device is idea.

### Use both Android and iOS?

Yubikey NEO + VASCO DigiPass SecureClick.

-------

Table of Contents

* [A note on U2F + TOTP devices](#multifunction)
* [USB Devices](#usb)
   * [Yubico U2F Security Key](#yubicou2f)
   * [Thetis U2F Security Key](#thetis)
   * [Feitian ePass](#epass)
   * [Bluink](#bluink)
   * [U2F Zero](#zero)
   * [KEY-ID FIDO U2F Security Key](#keyid)
   * [HyperFIDO Mini](#hypermini)
   * [HyperFIDO U2F Security Key](#hyper)
   * [Plug-Up Card Key](#plugup)
   * [YubiKey 4, 4C and Nano](#yubikey)
   * [YubiKey NEO](#neo)
 * [NFC-only Devices](#nfc)
   * [Fidesmo Card](#fidesmo)
   * [SurePassID TapID Card](#tapid)
 * [Bluetooth Low Energy Devices](#ble)
   * [Feitian MultiPass](#multipass)
   * [VASCO DigiPass SecureClick](#secureclick)

## <a name="multifunction"></a>*A note on multifunction U2F+TOTP devices*

I love U2F and use it everywhere I can.  Unfortunately, that is very few places and, with a few exceptions, mostly only on Chrome on desktop computers.  I have more TOTP (aka 'code generator' / 'authenticator app' / OATH) credentials than U2F registrations, and I have a TOTP credential set up for every site where I have a U2F registration, for use where U2F isn't available.  For me, this means that the devices (the more expensive Yubico ones and the Fidesmo card) that support a hardware-based TOTP app on the same device are far more useful for an advanced user like myself who enables 2FA everywhere than is a U2F-only device. The ability to get these codes via NFC with the Yubico Authenticator app on Android is particularly convenient and secure.

I am dilligent and always register my new seeds redundantly on two devices, so loss or failure of one doesn't leave me locked out, and I also keep a few of my most used seeds in the DUO app on iOS.  This strategy also makes moving between devices or getting a new phone a lot easier, since the most popular OATH apps don't have great backup/restore/export functionality.

If you are a sophisticated user of two-factor auth, it is well worth spending the extra money to get TOTP functionality even if you don't plan to use any of the other SmartCard or PGP features.

-------------
# <a name="usb"></a> USB Devices

## <a name="yubicou2f"></a>Yubico U2F Security Key

![Yubikey](https://www.yubico.com/wp-content/uploads/2015/04/Security-Key-by-Yubico-1000-2016-444x444.png)

*Review Author: Brad Hill*

**Brand:** Yubico

**Firmware:** Yubico

**Chip:** NXP

**Connection:** USB-A

**Features:** U2F only

**Price:** $18

**Buy:** [Yubico Store](https://www.yubico.com/store/)

Very reliable, from the co-originators of the technology.  Implements the specification faithfully, has a reliable attestation certificate, physically resilient.  Yubico devices are generally a good bet for corporate deployments where you want to check attestation to ensure that a real hardware device is being used, but also a solid general consumer choice.

Metadata for all Yubico devices can be found here: https://developers.yubico.com/U2F/yubico-metadata.json

The blue security key is among the most expensive of the devices that only does U2F, but I've used many of them and never heard of a defect.

If you're giving a U2F device to a non-technical person, I recommend this one over the more expensive Yubico devices because (as described below) the multifunction devices occasionally ship without U2F mode enabled, which is confusing and may be beyond the person's ability to self-remedy.  No mistakes are possible with the blue, U2F-only devices.

**Full Disclosure:** I have at various times received complimentary Yubico devices from both Yubico and Google.

-----------

## <a name="thetis"></a>Thetis U2F Security Key

![Thetis](/thetis.jpeg)

*Review Author: AGL*

**Brand:** Thetis

**Firmware:** Excelsecu

**Chip:** ?

**Connection:** USB-A

**Features:** U2F

**Price:** $13.95

**Buy:** [Amazon](https://www.amazon.com/Thetis-Universal-Authentication-Protection-SalesForce/dp/B06XHTKFH3/ref=sr_1_4?s=electronics&ie=UTF8&qid=1503019143&sr=1-4&keywords=U2F)

This security key is fashioned more like a USB thumb drive. The plastic inner part rotates within the outer metal shell and so the USB connector can be protected by it. The button is in the axis and is clicky, rather than capacitive, but doesn't require too much force to press. If you'll be throwing your security key in bags and worry about damaging them then perhaps this one will work well for you.

A minor nit is that the attestation certificate is signed with SHA-1. That doesn't really matter, but it suggests that the firmware writers aren't paying as much attention as one would hope. (I.e. it's a [brown M&M](http://www.snopes.com/music/artists/vanhalen.asp).)

----------

## <a name="epass"></a>Feitian ePass
![ePass](/ePass.jpeg)

**Brand:** Feitian

**Firmware:** Feitian

**Chip:** NXP

**Connection:** USB-A, NFC

**Features:** U2F, OATH HOTP (USB only), CCID

**Price:** $13.95

**Buy:** [Amazon](https://www.amazon.com/Feitian-ePass-NFC-FIDO-Security/dp/B01M1R5LRD/ref=sr_1_5?s=electronics&ie=UTF8&qid=1503019143&sr=1-5&keywords=U2F)

*Review Author: AGL*

This one is very much like the Yubico, just a little fatter around the middle. Otherwise, it's also a sealed plastic body and capacitive touch sensor. The differences are a dollar and NFC support—which should let it work with Android. However, I haven't tested this feature.

I don't know what the opposite of a brown M&M is, but this security key is the only one here that has its metadata correctly registered with the [FIDO Metadata Service](https://fidoalliance.org/mds/).

*Additional comments from Brad Hill:*

The ePass I bought on Amazon works well over NFC, but the USB interface never worked for me.  There is Windows-only management software for these devices, but it is a bit rough for non-Chinese users, and I wasn't able to successfully enable the USB U2F onnectivity, so perhaps it is a manufacturing defect.  Supposedly these devices also have an HOTP applet and JavaCard CCID functionality available over USB, but I've not used it. It is not compatible with the Yubico NFC protocol for TOTP.

----------

## <a name="bluink"></a>Bluink Key
![ePass](/bluink.jpeg)

**Brand:** Bluink

**Firmware:** N/A (running on phone)

**Chip:** N/A (running on phone)

**Connection:** USB-A

**Features:** U2F, TOTP, passwords

**Price:** $29.99

**Buy:** [Bluink](https://bluink.ca/buy)

*Review Author: AGL*

The [Bluink Key](https://bluink.ca/key) is quite different from the others here in that it's a USB device that acts as a front for an app running on a nearby phone (connected over Bluetooth). The USB device can act as a U2F device, but also as a keyboard (for “typing” passwords) and even as a mouse (for controling a desktop mouse via touch input on a phone, if that's useful to you).

I tested with the iOS app and the Bluetooth pairing worked well. The app requires a password, but can be configured to accept TouchID. Once paired, the USB dongle acts as a U2F device and creating a key makes the phone vibrate for confirmation. U2F keys can be named and are listed in the app. Authenticating with a key similarly prompts for confirmation via the app.

When I first set it up, it was just for testing so I ignored the warning about creating a backup. That was a mistake. Once paired with the app, the USB dongle will reject future pairing requests unless you know the pairing code from the app. That makes a lot of sense—after all, it's a Bluetooth device that can act as a keyboard. But it does mean that if you delete the only copy of the pairing code by uninstalling the app (as I did), then the dongle cannot be used. So you should be sure to create a backup when prompted and to save it somewhere. (To restore, open it in the Files app and “share” with the Bluink app. You'll need the password in use when the backup was created.)

I didn't find any issues when testing the U2F implementation, save for the fact that registration messages seem to require a bit to be set that Chrome sets, but which the spec says shouldn't be required. As a plus, since I believe that the U2F protocol is implemented in the app, that means that it can be easily fixed and updated. (I didn't test the signature generation as extensively as some of the other tokens since a full test requires around 1000 signatures and that wasn't really viable here.)

As hinted, the Bluink key also allows passwords to be generated and stored, and supports TOTP. Both of these can be “typed” for you via the dongle. See the [user manual](https://bluink.ca/files/BluinkKeyUserGuide.pdf) for more details on the non-U2F aspects of this device.

----------

## <a name="zero"></a> <a name="yubicou2f"></a>U2F Zero
![zero](/zero.jpeg)

**Brand:** Conorco

**Firmware:** Conor Patrick

**Chip:** Atmel

**Connection:** USB-A

**Features:** U2F

**Price:** $8.99

**Buy:** [Amazon](https://www.amazon.com/U2F-Zero/dp/B01L9DUPK6)

*Review Author: AGL*

It's the only token on Amazon that has open source firmware (and hardware designs), and that was worth waiting for. It's also the cheapest of all the options here.

Sadly, I have to report that I can't quite recommend it because, in my laptop (a Chromebook Pixel), it's not thick enough to sit in the USB port correctly: Since it only has the “tongue” of a USB connector, it can move around in the port a fair bit. That's true of the other tokens too, but with the U2F Zero, unless I hold it just right, it fails to make proper contact. Since operating it requires pressing the button, it's almost unusable in my laptop.

However, it's fine with a couple of USB hubs that I have and in my desktop computer, so it might be fine for you. Depends how much you value the coolness factor of it being open-source.

*Additional comments from Brad Hill:*

A cool little device, and sturdier than it looks. I'm encouraged that they can source the materials, at hobbyist scale, for around $6, so there is definitely room for prices of more polished and mass produced devices to come down.  I have the first version of this device, which suffers from some serious defects: First, it generates a device-specific attestation key, which makes it trackable cross-domain. Second, it only stores up to 8 registrations. You can use a Linux-only utility to clear the key storage but you have to delete them all.  I understand the latest versions now use a key wrapping algorithm like the Yubico devices that addresses this limitation; unfortunately the firmware isn't upgradable.  I can't recommend the original version for more than technical curiosity.

-------------

## <a name="keyid"></a> KEY-ID FIDO U2F Security Key
![key-id](/keyid.jpeg)

**Brand:** KEY-ID

**Firmware:** Feitian(?)

**Chip:** ?

**Connection:** USB-A

**Features:** U2F

**Price:** $9.95

**Buy:** [Adafruit](https://www.adafruit.com/product/3363)

*Review Author: AGL*

I photographed this one while plugged in in order to show the most obvious issue with this device: everyone will know when you're using it! Whenever it's plugged in, the green LED on the end is lit up and, although the saturation in the photo exaggerates the situation a little, it really is too bright. When it's waiting for a touch, it starts flashing too.

In addition, whenever I remove this from my desktop computer, the computer reboots. That suggests an electrical issue with the device itself—it's probably shorting something that shouldn't be shorted, like the USB power pin to ground, for example.

While this device is branded “KEY-ID”, I believe that the firmware is done by Feitian. There are similarities in certificate that match the Feitian device and, if you look up the FIDO certification, you find that Feitian registered a device called “KEY-ID FIDO® U2F Security Key”. Possibly Feitian decided against putting their brand on this.

**Based on further testing from AGL (https://www.imperialviolet.org/2017/10/08/securitykeytest.html) this device is not recommended as the key handle allows a site to associate multiple accounts to the same physical device.**

*Additional comments from Brad Hill:*

I've used and given away a number of these because of their attractive price point and not heard of the reboot issues AGL describes above manifesting on MacBooks.

----------

## <a name="hypermini"></a> HyperFIDO Mini
![HyperFIDO Mini](/hypermini.jpeg)

**Brand:** HyperFIDO

**Firmware:** Feitian(?)

**Chip:** ?

**Connection:** USB-A

**Features:** U2F

**Price:** $13.95

**Buy:** [Amazon](https://www.amazon.com/HyperFIDO-Mini-U2F-Security-Key/dp/B01LZO0WE9)

*Review Author: AGL*

By observation, this is physically identical to the KEY-ID device, save for the colour. It has the same green LED too (see above).

However, it manages to be worse. The KEY-ID device is highlighted in Amazon as a “new 2017 model”, and maybe this an example of the older model. Not only does it cause my computer to reliably reboot when removed (I suffered to bring you this review, dear reader), it also causes all devices on a USB hub to stop working when plugged in. When plugged into my laptop it does work—as long as you hold it up in the USB socket. The only saving grace is that, when you aren't pressing it upwards, at least the green LED doesn't light up.

-------------

## <a name="hyper"></a> HyperFIDO U2F Security Key
![HyperFIDO](/hyper.jpeg)

**Brand:** HyperFIDO

**Firmware:** Feitian(?)

**Chip:** ?

**Connection:** USB-A

**Features:** U2F

**Price:** $9.98

**Buy:** [Amazon](https://www.amazon.com/HyperFido-K5-FIDO-U2F-Security/dp/B00WIX4JMC/ref=pd_bxgy_229_img_2?_encoding=UTF8&psc=1&refRID=Q4CAYP6B64ESGRPH5PG9)

*Review Author: AGL*

This HyperFIDO device is plastic so avoids the electrical issues of the KEY-ID and HyperFIDO Mini, above. It also avoids having an LED that can blind small children.

However, at least on the one that I received, the plastic USB part is only just small enough to fit into a USB socket. It takes a fair bit of force to insert and remove it. Also the end cap looks like it should be symmetrical and so able to go on either way around, but it doesn't quite work when upside down.

Once inserted, pressing the button doesn't take too much force, but it's enough to make the device bend worryingly in the socket. It doesn't actually appear to be a problem, but it adds a touch of anxiety to each use. Overall, it's cheap and you'll know it.

**Based on further testing from AGL (https://www.imperialviolet.org/2017/10/08/securitykeytest.html) this device is not recommended as the key handle allows a site to associate multiple accounts to the same physical device.**

*Additional comments from Brad Hill:*

There is funny stuff going on with how the several of these I have present their attestation.  Every time the device is registered, they generate a unique device name as part of the certificate.  This has the upside of not presenting a cross-domain tracking identifier, but it tells me that the attestation private key is in the device somewhere. (or it may be generating a new random attestation key and cert every time, I don't recall)  Anyway, they seem fine for consumer use - I've used one I leave installed in my monitor's USB hub on a daily basis for almost a year now.  But I wouldn't recommend these if you care about checking attestations.

--------------

## <a name="plugup"></a> Plug-Up Card Key
![plug-up](/plugup.jpg)

**Brand:** Plug-Up

**Firmware:** Plug-Up

**Chip:** ?

**Connection:** USB-A

**Features:** U2F

**Price:** N/A

**Buy:** [Amazon](https://www.amazon.com/Plug-up-International-U2F-SK-01-FIDO-Security/dp/B00OGPO3ZS/ref=sr_1_1?ie=UTF8&qid=1503085374&sr=8-1&keywords=plug-up+u2f)

*Review Author: Brad Hill*

I've seen these mentioned a number of times and used in press photos.  They are printed in a 1mm-depth credit-card format which you punch out and fold over to form the key.  I have two from 2014, keepsakes of the FIDO plenary in Paris.  These don't have a button, you must physically insert and remove the key every time.

The key I used sucessfully in my Chromebook at that time hasn't worked for several years now.  I don't know if that's due to protocol changes or manufacturing quality.  As much as I like the idea of keys cheap enough to give away, I'm not sure I'd recommend these, because the accounts you'll be protecting with them are quite valuable, and it would be a shame to be locked out because a $5 piece of cheap hardware failed.  At any rate, it doesn't seem that Plug-Up is still manufacturing these, so this is mostly a historical curiousity.

**Full Disclosure:** These devices were given to me by Plug-Up.

-------------

## <a name="yubikey"></a> YubiKey 4, 4C and Nano
![4 and nano](/4-nano.jpg)
![4C](/4c.jpeg)

**Brand:** Yubico

**Firmware:** Yubico

**Chip:** NXP

**Connection:** USB-A (4 and Nano), USB-C (4C)

**Features:** U2F, TOTP, Yubico OTP, PGP, PIV/CCID

**Price:** $40 / $50 / $50 

**Buy:** [Yubico Store](https://www.yubico.com/store/)

*Review Author: Brad Hill*

*4C Photo Credit: AGL*

I'll review these together as they are essentially the same device in different packaging.  These have the same solid U2F implementation as the U2F-only key, plus a bunch of additional features.   My favorite is the TOTP applet, accessible though the [Yubico Authenticator](https://www.yubico.com/support/knowledge-base/categories/articles/yubico-authenticator-download/) application for Linux, Windows and Mac.  I like having hardware TOTP key storage and backup, as I discuss in more detail below, so this is a killer feature for me.

I'm also interested in trying out the PGP features of the key for code signing on GitHub, though I otherwise try to avoid PGP.

Regarding the packaging, the 4 has the standard tried-and-true Yubikey packaging.  The 4C is a bit thicker.  I have heard reports that the first generation of the 4C devices do not withstand everyday carry on a keychain; hopefully current models are more durable. (I don't have one.) The Nano is a great choice to leave in your computer, monitor or other hub full-time, easily accessible with just a tap.  I tried carrying a Nano with a small USB-C adapter on my keys for a few weeks, but the tiny bit of metal where a nylon camera-loop attachment goes tore out.  It would be a big bummer to lose a $50 device and the associated credentials this way, so I can't recommend the Nano as an everyday carry device.

*Troubleshooting:* 

I've had friends that purchased YubiKeys of these makes occasionally report that they don't work with U2F websites.  This has always been due to the fact that these devices have several ways in which they can be configured (proprietary OTP, U2F and PIV/CCID) and the U2F mode was somehow turned off when it shipped to them. You can use the [YubiKey Personalization Tool](https://www.yubico.com/support/knowledge-base/categories/articles/yubikey-personalization-tools/) to make sure the U2F attachment mode is enabled. (If you're generous enough to be giving away $40 devices, you might want to double-check this first.)

Some people using the Nano have complained that it constantly blinks the LED at a slow interval when inserted.  If this bothers you, disabling the PIV/CCID attachment mode with the Personalization Tool will stop this, and the LED will only blink (rapidly) when waiting a U2F touch.

*Infineon RSA Key Generation Flaw:*

In October, it was revealed that Infineon TPM chips, upon which the Yubikey 4 series is based, had a serious flaw in RSA key generation that allows many keys to be factorable much more quickly than should be possible.  _This does not affect the U2F or TOTP functions of these devices at all._  If you use the PGP or PIV functions of your Yubikey 4 device, you should check here if yours is vulnerable.  Yubick offers a replacement to all customers impacted. https://www.yubico.com/keycheck/  

**Full Disclosure:** I have at various times received complimentary Yubico devices from both Yubico and Google.

---------------

## <a name="neo"></a> YubiKey NEO (Editor's Choice)
![NEO](/neo.jpg)

**Brand:** Yubico

**Firmware:** Yubico

**Chip:** NXP

**Connection:** USB-A and NFC

**Features:** U2F, TOTP, Yubico OTP, PGP, PIV/CCID

**Price:** $50 

**Buy:** [Yubico Store](https://www.yubico.com/store/)

*Review Author: Brad Hill*

This is shares all the features of the 4th generation YubiKeys above, but is a 3rd generation device so doesn't support the 4096 bit PGP features of the ones above.  On the other hand, it does U2F, TOTP and PGP over NFC, which is *the* killer feature if you are an Android user.

The Yubico Authenticator App for Android [ [Google Play Store](https://play.google.com/store/apps/details?id=com.yubico.yubioath&hl=en) ] allows you to save your TOTP seeds to the key's hardware with a tap, and access codes with another tap.  I love this feature so much.

The Yubikey NEO is my "daily driver", attached to my badge lanyard and used every day for several years.

**Full Disclosure:** I have at various times received complimentary Yubico devices from both Yubico and Google.

-------------

# <a name="nfc"></a> NFC-only Devices

I have two card form factor devices that do U2F over NFC only.  I really like them, but there are some important caveats I'll get to.  

Why do I like them?

* Easy to carry. They are the same dimensions (even thickness) as a credit card.
* Easy to use. The antenna in these devices is much more reliable than on the smaller form factor devices and often works without removing it from my wallet.  I keep my NFC buss pass on one side and my NFC U2F on the other side - NFC where # of cards >= 3 requires a higher-dimensionality wallet.
* No batteries.
* No additional registration process, moves seamlessly between devices.
* Familiarity.  I have high hopes for these as mass-market devices if some of the deployment concerns below can be addressed.  People are very used to using proxcards for mass transit, building access, and are getting accustomed to NFC for payments.  They have reliable and established habits for where to put and how to take care of valuable cards.
* Multi-use.  U2F can sit easily on top of standard SmartCard platforms that are ubiquitious and have a wide variety of other applications available, from transit passes to EMV payments and even bitcoin wallets.

Caveats?

* Android only, for now.  All iPhones have the necessary hardware and there are some moves towards opening APIs for NFC in iOS 11, so I hope this will bode well for the reach of NFC U2F.  It would also be nice to see NFC readers integrated into laptops, as it would be cheap and easy to do so.
* Registration difficulties.  https://m.facebook.com/ (not the app) and https://github.com work well, but while Google supports authenticating with NFC to your account natively in Android, at the time of this writing, you can only add a new U2F device to your account using desktop Chrome, which only supports USB.  So, you can use NFC with a multi-attachment device like the YubiKey NEO or Feitian MultiPass that was registered over USB first, but you can't use one of the card devices below with your Google account.  I hope they will fix this soon.  These devices have or are available with smartcard chip physical interface, but I don't have compatible reader hardware to test if this can be used to bypass this registration difficulty.


## <a name="fidesmo"></a> Fidesmo Card (Editor's Choice)
![Fidesmo Card](/fidesmo.jpg)

**Brand:** Fidesmo

**Firmware:** Fidesmo

**Chip:** ? (probably a standard JavaCard chip)

**Connection:** NFC

**Features:** U2F, TOTP, PGP, Bitcoin wallet, more

**Price:** 10-15 EUR, plus additional for extra loadable apps 

**Buy:** [Fidesmo Store](http://shop.fidesmo.com/)

*Review Author: Brad Hill*

A great device at a great price. The Fidesmo card is standard JavaCard hardware with custom firmware on top and an app store for Android [ [Google Play Store](https://play.google.com/store/apps/details?id=com.fidesmo.sec.android) ] that allows loading various modules that can be used over NFC. (or, for a few Euros more, through the physical chip-card interface, but I haven't tried that)  I use the U2F and OTP applets, the latter of which is fully compatible with the Yubico Authenticator app for Android. There are also transit cards, a bitcoin wallet, a PGP app and more available, each for a few Euros.

The physical interface version of this card doesn't expose U2F over USB, according to reader reports - U2F is still NFC only.

I keep this in my wallet and backup all my TOTP seeds to it, in addition to my YubiKey NEO. I really can't say enough good things about this device, I just wish I could register NFC devices directly to my Google account.

The dual-interface cards are available blank and can be custom-printed. If you want a low-profile device for crossing a border, you might dress it up as a bus pass or similar.

-------------

## <a name="tapid"></a> SurePassID TapID Card
![TapID](/surepassid.jpg)

**Brand:** SurePassID

**Firmware:** SurePassID

**Chip:** ? (SurePassID also sells the "TapID Treo" that looks like a re-branded Feitian ePass, so maybe Feitian?)

**Connection:** NFC

**Features:** U2F, more?

**Price:** $19.95

**Buy:** [Amazon](https://www.amazon.com/Account-Security-Android-Two-Factor-Authentication/dp/B01LY2PLOX/ref=sr_1_2?s=electronics&ie=UTF8&qid=1503093547&sr=1-2&keywords=SurePassID+U2F)

*Review Author: Brad Hill*

U2F over NFC works.  I haven't tried to do much else with this card.  The manufacturer's website says there is a combo card available that does both EMV payments and U2F, which sounds neat.  This card has a physical chip interface as well, but I have only used the NFC interface.  They are available from 3rd party sellers on Amazon for $20 plus S&H, but it seems like they are mostly intended for bulk purchase direct from the manufacturer.  They also mention some interesting [support software](https://www.surepassid.com/fido-u2f-solutions/) on the manufacturer website like a Windows Login Credential Provider, Linux PAM/SSH library, FIDO integration for Outlook Web Access and more, so this might be a very interesting choice to investigate for a large enterprise deployment.

----------

# <a name="ble"></a> Bluetooth Low Energy Devices

Personally, I find BLE U2F to be painful. The pairing experience is not obvious, (it has to start from within an app, not like normal Bluetooth) needs to be done per-device, and requires entering a code.  Only Google has support for BLE authenticators, and I've found it consistently buggy on both Android and iOS.  I have to make multiple attempts to register a new BLE authenticator on Android, and have not successfully completed a registration / authentication on iOS with SmartLock yet with either style of device I own.  If you're hoping to deal with the USB-C issue of your new MacBook via BLE, don't get your hopes up there, either - Chrome desktop doesn't interact with BLE authenticators yet.  Finally, as of the time I tried, you can't add a BTLE (or NFC) key to your Google account directly, you can only authenticate with one you've registered over USB in Chrome on the desktop. So you need to register it with a PC/Mac before you can use it with your mobile device.

I hope we'll see some rapid progress on this front and I can just keep a "magic button" on my keys in my pocket soon, that I press to authenticate anywhere without dongles or adapters, but I'm not holding my breath.

**Update, 9/26/2017:**  The U2F experience in Android O, now provided through Google Play Services, is much improved for using BTLE and I've been able to successfully both register and authenticate with multiple types of BTLE authenticator to Facebook.

-----------

## <a name="multipass"></a> Feitian MultiPass
![MultiPass](/multipass.jpg)

**Brand:** Feitian

**Firmware:** Feitian

**Chip:** NXP

**Connection:** USB-A, NFC, BLE 

**Features:** U2F

**Price:** $24.99

**Buy:** [Amazon](https://www.amazon.com/Feitian-MultiPass-FIDO-Security-Key/dp/B01LYV6TQM/ref=sr_1_6?s=electronics&ie=UTF8&qid=1503019143&sr=1-6&keywords=U2F)

*Review Author: Brad Hill*

This is the only device I've seen that supports all three major connectivity modes. It has a micro-USB interface that can be used (with an adapter cable) to register it with your Google account in Chrome, use it on PCs, and the battery for the BTLE also recharges through that USB port. The form factor is nice and durable and it fits well on a keychain.

I tried on several iOS devices to use the BTLE interface with Google SmartLock, but was never able to see the device from iOS.  It works on Android after a few tries, but the responsiveness is very poor - pairing and authentication operations take a long time to complete.

There is an NFC interface on this device.  It works with Android, but the antenna is very bad and it requires knowledge of the exact position of the antenna on your phone and a lot of patience to make it actually work.

This key does not support the Yubico TOTP over NFC protocol.

I put this on a keychain when I bought it, expecting it to be my new "daily driver", but the fiddly NFC antenna, lack of NFC TOTP support, and my overall disappointment so far with BLE means it now it stays in my bag as an emergency backup.

Additional information can be found here: https://github.com/Manouchehri/Feitian-MultiPass-FIDO-U2F

---------------
## <a name="secureclick"></a> VASCO DIGIPASS SecureClick
![SecureClick](/secureclick.jpg)

**Brand:** VASCO

**Firmware:** VASCO

**Chip:** ? (VASCO?)

**Connection:** USB-A and BLE

**Features:** U2F

**Price:** $39.00 (US), £32.21 (UK)

**Buy:** [Amazon US](https://www.amazon.com/DIGIPASS-SecureClick-FIDO-U2F-Security/dp/B01M0DPK3K/ref=sr_1_1?ie=UTF8&qid=1505832277&sr=8-1&keywords=secureclick), [Amazon UK](https://www.amazon.co.uk/VASCO-DATA-SECURITY-DIGIPASS-SecureClick/dp/B01M0DPK3K/ref=sr_1_1?ie=UTF8&qid=1503188198&sr=8-1&keywords=vasco+secureclick)

*Review Author: Brad Hill*

This is a Bluetooth Low-Energy U2F device.  It is about the diameter of a American Quarter, and about the thickness of an UK Pound coin.  It comes with silicone keychain sleeves in three colors and a USB-A tranciever for use on desktop computers.

To register the device, you first need to attach the tranceiver to a desktop/laptop computer and run the DIGIPASS SecureClick Manager app from the Chrome app store to pair the tranceiver to your device. 

https://chrome.google.com/webstore/detail/digipass-secureclick-mana/gjbcaijefcocakonhdnfhomcnlcppbcg?hl=en  

After it is paired, you can register it to your Google account with a desktop version of Chrome and then use it on Android or iOS (using Google's Smart Lock app).  I can confirm I have successfully used this device to enroll an account in Google Advanced Protection and then authenticate on an iPhone.

For Facebook, you can use it standlone with a mobile device - registration and authentication are both supported natively at https://m.facebook.com/new_sec_settings/security_keys/  (The Facebook native apps don't support U2F yet and there is no way to use U2F on iOS with Facebook.)



The unit uses an included CR2012 battery, which should last at least two years when used for maximum of 10 authentications per day. The battery is replacable, and instructions for doing so are in the manual.

*Troubleshooting:* 

The BLE pairing experience instructs you to enter a code "printed on the device".  There is no code, but '000000' (six zeros) works.

On my USB-C MacBook Pro, I noticed that the USB-A tranceiver would only work when connected directly with an adapter cable.  When I plug it into the USB hub on my montior, it doesn't function.  This is sad because it makes it inconvenient to keep the tranceiver plugged in at my desk and use the same device for desktop + mobile.  (I leave other USB-A U2F keys permanently in my monitor hub and they work fine.)

**Full Disclosure:** I received several of these devices for evalutation courtesy of VASCO.

----------
