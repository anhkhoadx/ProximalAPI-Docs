#Proximal API v2.0

##Overview

###Introduction

The Wireless Registry Proximal API enables the association of content to wireless ID strings and the subsequent retrieval of that content. Content is associated via The Wireless Registry registration portal by owners of wireless ID strings, or directly via the Proximal API by anyone. Wireless devices generally detect Wireless Names and Hardware IDs from the signals around them in a range of combinations. These signals can vary from Wi-Fi names, Bluetooth names, and MAC addresses, to BLE beacon IDs, RFID numbers, and a number of similar wireless expressions and IDs yet to come via new technologies and standards. The Wireless Registry’s Proximal API is the first open API to allow any device to both create and retrieve associations to any signal, while at the same time respecting an industry-approved opt-out mechanism. It gives the registered owners of these signals full control over any and all associated content. 

Use of The Wireless Registry Proximal API is subject to the terms of the API License Agreement. For questions and support, please email contact@wirelessregistry.com.

###Definitions
    
The Proximal API makes use of the following concepts defined below: wireless name, hardware ID, and pin.
  
####1. Wireless Name

**a) Wi-Fi and Bluetooth Name**
 
A Wireless Name is a word or phrase, often readable, transmitted from a wireless device as an ID string or as a form of device or network identification. The Proximal API currently responds to wireless names 1 to 32 characters (32 bytes) in length that typically correspond to the Service Set Identifier (SSID) of a Wi-Fi or Bluetooth device. SSIDs are often referred to as “network names” and are broadcast by a device to all receiving devices within the broadcast radius of the device’s networking hardware.

A new device typically has an SSID that is set by default by its manufacturer. The SSID can be manually changed on a number of devices, such as smartphones, tablets, laptops, PCs, and home or office wireless network routers. You can register the wireless name already used by a device, or register a preferred wireless name and change the name on the device accordingly. Many devices can use the same name, but a particular name can only have one owner. A number of devices (such as routers) can transmit several or many wireless names simultaneously. The Proximal API accepts a wide variety of wireless name strings that may be detected in real use situations.

**b) BLE Beacon Identifier**

The second major group of wireless names to which the API responds are Bluetooth Low Energy (BLE) or Bluetooth Smart identifiers. The first format accepted is the common BLE ID format (Type1), which is generally recognized as iBeacon(TM) (trademark of Apple Corp). This type of proximal signal is usually used in low-cost BLE transmitters that mobile devices can detect and use to initiate functions in a mobile app. The Wireless Registry is the first time that Beacon IDs can be registered and their signals associated to meaning and content across devices and across apps. Any device that detects the beacon ID can check the Proximal API for that content and contribute to it. Beacon owners control their transmitted beacon IDs and the content associated to them.

Any Beacon UUID can be registered. The UUID format is a 16 byte ID string entered at hexadecimal digits in the format: 12345678-ABCD-1234-ABCD-123456ABCDEF, and followed by two 16 bit characters expressed as integers: Major (0-65535) and Minor (0-65535). The three components are separated by the ~ separator.

    Example of an iBeacon Wireless Name:

    E2C56DB5-DFFB-48D2-B060-D0F5A71096E0~00000~00000

See http://en.wikipedia.org/wiki/iBeacon for more details about about Apple Inc.’s beacon technology. Other beacon formats are either in use today or will be released shortly in the rapidly growing field of proximal beacons.

**c) LTE Direct Expression**

The Proximal API, when applied to LTE Direct, is referred to as an Expression Name Server. The Wireless Registry is working with partners to demo the Expression Name Server in future.

####2. Hardware ID

In the current release, our system supports two main types of hardware IDs:

**a) MAC address**

The most common hardware ID used by our system is the **media access control address** (**MAC address**), one of the most frequently detected wireless ID signals today. It is a unique identifier assigned to network interfaces in most IEEE 802 network technologies, including Ethernet. In Wi-Fi and Bluetooth devices, the MAC address is transmitted around the device to identify it to other devices in the immediate area.
  
There are many ways of writing a MAC address. For ease of reading, our system converts all valid MAC addresses to what we call _the normalized version_. This is a variant of the standard IEEE 802, with six groups of capitalized hexadecimal digits, separated by colons (:) in transmission order.

    A normalized MAC address:

    01:23:45:67:89:AB

We also accept other formats, although these converted to the normalized version:

    Other accepted MAC address formats:

    01:23:45:67:89:ab
    01-23-45-67-89-ab
    0123456789ab
    0123.4567.89ab

See http://en.wikipedia.org/wiki/MAC_address for more details about MAC addresses.

**b) IMEI**

The International Mobile Station Equipment Identity (IMEI) is a number, usually unique, that identifies most mobile phones (i.e., GSM, UMTS, LTE and iDEN), as well as some satellite phones. It is usually found printed inside the battery compartment of the phone, but can also be displayed on-screen on most phones by entering *#06# on the dialpad, or alongside other system information in the settings menu on smartphone operating systems.

As of 2004, the format of the IMEI is AA-BBBBBB-CCCCCC-D, where all the digits are decimal. However, The Wireless Registry uses a slightly different version, replacing the "-" (dash) separator with "~" (tilde) for identification and clarity.

    AA~BBBBBB~CCCCCC~D

See http://en.wikipedia.org/wiki/IMEI for more details about IMEI.

**c) Other hardware IDs**

Wireless names go together with hardware IDs. The Wireless Registry's system is flexible, allowing new hardware ID formats to be published as they become available.

####3. Pin

A pin is an information token that is attached to a wireless name or a hardware ID, or a combination of both wireless name and hardware ID. Pins are the basic unit that is accepted by the API. Pins are text strings of 1-65K characters in length, and while standard pin types expect linkages to the content matching that pin type, custom pins can hold any combination codes and information that a developer wishes to use. A wide range of innovative use-cases are possible.

Developers can pin codes that represent content on their servers, whereby an instance of their application can check surrounding detectable signals and retrieve codes left on those signals by other instances of that application. This provides app-to-app communication, without GPS or check-ins, cross-device and cross-app, and in many different combinations.
 
Some developers attach lists of wireless identifiers of one type to wireless identifiers of another type - so the detection of a Wi-Fi signal might reveal a list of NFC codes in a room pinned by another device which detected both.

#####Pin Security and Treatment

The Wireless Registry Proximal API respects the world's first industry-driven proximal signal privacy and opt-out system, managed by the Future of Privacy Forum in Washington, DC. Mobile location analytics companies from around the world participate by respecting the privacy preferences of individuals who opt out their proximal signals. Developers using the Proximal API are **automatically covered by this industry-leading privacy best practice**. See www.futureofprivacy.org for more information.
 
The Proximal API is also the first to be integrated into The Wireless Registry Inc. system of wireless name and ID registration. This allows individuals and businesses around the world to register wireless names and ID strings that they own and that represent them. The Proximal API **respects the content managed by signal owners**, as well as their privacy settings.
 
The Proximal API is un-metered and free. The system is supported via The Wireless Registry ownership model rather than an API usage-based model.

#####Pin Types

The system supports three main categories of pins: **standard pins**, **profile pins**, and **custom pins**. Standard and profile pins are secured via the wireless name owner's complete control over all standard pins through the registration portal, regardless of their source. Custom pins are secured via each developer using complex and secure pin types that they manage. However, wireless name and hardware ID owners can still remove all data from their signals, including custom pins, which are then moved to suitable alternatives.

**a) Standard pins**

Standard pin types are defined by The Wireless Registry, with clear rules and restrictions for each standard type. They are _always_ visible on our portal (https://reg.wirelessregistry.com) and are therefore not suited for private information.

The system currently supports the following standard pin types:

PIN TYPE | DATA TYPE | DATA CONTENT VALUE(s) | DESCRIPTION
-------- | --------- | -------- | -----------
**image** | _text_ | max 65K chars | The path to an image file. Usually hosted on imgur.com, although any other server or image hosting service can be used.
**text** | _text_ | max 65K chars |Generic textual message.
**url** | _text_ | max 65K chars | Generic URL path.
**streamingMedia** | _text_ | max 65K chars | URL path to a streaming audio or video resource: YouTube, Vimeo, etc.
**latLongSurvey** | _number/number_ | number/number, latitudes (-90 to 90), longitudes (-180 to 180), south latitudes and west longitudes having a minus sign  (five to nine digit precision, such as 38.90970230, recommended) | Generally a simple lat-long pinned from any mobile app. Note these pins are crowd-contributed. See profile pins below for a related lat-long type.

Standard pins must be created on a single wireless name or wireless name ~ hardware ID combination at a time. For example, a standard pin could be pinning a photo to the wireless name of a restaurant. Any app on any device could check the Proximal API for content associated with that restaurant's wireless name, immediately get the pin, and then render the photo.

**Note:** The Proximal API can also be queried with no pin type parameter specified. It will respond with all standard pins associated to the checked wireless name(s), but not with custom pins or profile pins.

Standard pins are publicly viewable unless deleted or blocked by the wireless name owner. When an application requests pins associated to a wireless name or hardware ID it encounters, it can request all standard (public) pins, or – in the interest of not being overwhelmed – it may request only a certain type of standard pin, such as streamingMedia. Because a large number of wireless names and hardware IDs can be checked at once (for example, 200 wireless names detected in a single location), pin types can be used to refine the search to the app developer’s needs.

**b) Profile pins**

Profile pins are similar to standard pins, except that they are read-only. Profile pins are managed either by The Wireless Registry registrants through The Wireless Registry registration portal, or via an authorized third-party registrar. Queries for profile pins must specify the pin type (they are not returned on a query with a blank pin type). Profiles pins and pin values cannot be edited or added via the Proximal API.

The system currently supports the following profile pin types:

PIN TYPE | DATA TYPE | DESCRIPTION
-------- | --------- | --------
**profile** | _text_ | Returns all profile items associated to a wireless name by the registered owner — all items in this list.
**profileName** | _text_ | Any wireless signal can be checked for a Wireless Name it is linked to. This is helpful for hardwareIDs such as MAC addresses detected without wirelessNames or BLE Beacons detected without readable names.
**profileDescription** | _text_ |
**profilePicture** | _url_ | Imgur url.
**profileFacebook, profileTwitter, profileLinkedIn, profileGoogle+, profilePinterest** | _social_ _account url_ | Facebook, Twitter, Linkedin, Google+, Pinterest custom URL (all four can exist at once).
**profileUrl** | _url_ | Any custom url chosen by the name owner.
**profileEmail** | _email_ | Email address if the owner has decided to share.
**profilePhone** | _phone number_ | Phone number if the owner has decided to share.
**hardwareDefinition** | _url_ | HardwareIDs may have a hardware definition such as a Wolfram Connected Devices URL: http://devices.wolfram.com/devices/vitagoods-wrist-bluetooth-travel-blood-pressure-monitor-vs-4300.html.
**registeredLatLong** | _number/number_ | An owner may specify a lat-long they wish to associate with registered beacon IDs. Latitudes (-90 to 90), Longitudes (-180 to 180). Beacon IDs may have values available.
**bleMacAddress** | _0123456789ab_ | Some registered beacon IDs may have MACs associated to them by their owner.
**linkedName** | _string_ | Returns the Name linked to the Mac or beacon (only for Verified MACs and beacons).
**profilePublicName** | _string_ | Returns the Public Name of the user account linked to the Mac or beacon.

**c) Custom pins**

In addition to the standard pin types, we also allow custom pin types to be set up 
In addition to the standard and profile pin types, The Wireless Registry Proximal API users may also create custom pin types. These never appear on our portal and can only be displayed in third-party applications, via the Proximal API.

Unlike standard and profile pin types, custom pins are inherently definite and secure. They require the single and specific custom pin type of interest to the developer (usually defined by the developer) amid a group of wireless names or IDs detected by the device running the application.

A custom pin type's length is restricted to between 25 and 255 characters. No custom type pin of fewer than 25 characters is permitted, because that space is set aside for additional expansion of the standard pin types. As with standard pin types, however, the content field has a maximum of 65K characters.

Custom pin types are defined by the Proximal API user. Pins cannot be retrieved via the Proximal API unless the pin type is included in the query. In this way, custom pins can be kept private, with pin types known only to the developer. You can share your custom pin types with anyone you want to give access to your pins.

Custom pins can be created on an array of one to ten wirelessName, hardwareID, beaconID, or wirelessName~hardwareID combinations at a time. A custom pin, for example, could be an application pinning a message to the top five strongest MAC address signals in a room. Other instances of the same app can then retrieve that pin by checking all detected MACs against the Proximal API and with the correct, app-specific custom pin type known only to that app.

Unlike standard pins, custom pins cannot be retrieved without being explicitly requested in the query. The requester must know the custom pin type and query for that type. There are currently no pin type parameter ranges or wildcards.

**d) Group/pattern pins**

Custom pins to wireless ID string groups and patterns are in performance testing with partners.

#####Parameter Notes

**Pin use combinations**

When custom pins are associated with both stationary signals – such as Wi-Fi access points or beacons – as well as to the signals of moving devices – such as mobile MAC addresses and iPhone-based beacons – a wide range of new contextual awareness and device-to-device sharing of pin data becomes possible.

Creative uses of pins allow two mobile app installs to deduce that they are immediately proximal via detecting the same two or three ambient signals — quickly and without the need for GPS check-ins. Other applications pin custom triggers (such as game tokens) to ambient signals that persist for days (or months) and are detected by other running apps checking ambient signals. Still others pin usernames or statistics enabling devices to see how many users are currently (or have in the past been) in a given location over a certain period of time.

The Proximal API works in-flight with in-flight Internet, on moving buses and cars, or anywhere a data connection is available, without GPS or check-in, and without draining a mobile device's battery. 

**Date and time parameters**

Careful use of the startDate and endDate parameters on the GET functions will ensure recent or older pins are retrieved, or the correct count of pins for the time-frame of interest. The parameters avoid stale data (as relevant to any given application). Uses of CreatedAt date and time can, for example, indicate immediate proximity between two devices via the simultaneous detection of the same unique wirelessName~hardwareID combinations. Other functions can be built on top of two or more devices comparing the signals around them via rapid post- and get-pin comparisons. This process can be applied to a mix of Wi-Fi, Bluetooth, BLE, etc all at the same time.

**Parameter array size and multiple pins**

Several parameters are arrays that allow for large numbers of strings. For example, wireless devices may encounter and check 10-100 wireless names and MAC addresses in an array. The Proximal API adjusts its response output so a single pin is returned to represent multiple identical pins with identical addedDate(time/second). The wireless strings returning the same pin are listed in the output. Likewise, getCount will also return the full count of all pins, each counted individually.

For example, an application may pin a single custom pin to an array of ten detected wireless names (such as the ten strongest surrounding signals). It uses a single Proximal API create call to do so. A second device in the area, with the same application, submits a Proximal API get call to all 50 detectable surrounding wireless names. In response, it immediately receives the first device’s single pin (with the group indicated) — rather than ten identical pins — despite all ten MACs being in the array of the 50 total nearby checked MACs.

###Data Security

####Data Ownership

The Wireless Registry considers all data in the system to be owned and controlled by the registered wireless string owners. Registrants of a wireless name control all pins at all times. Hardware ID registrants similarly control all pins, both standard and custom pins. Developers can freely add pins to any wireless signal at no cost as well as query the system without restriction or cost. The Wireless Registry and its Proximal API infrastructure will automatically ensure the pins respect the privacy and control settings of all wireless name and hardware ID owners.

Wireless names or hardware IDs that have been opted out will cause standard pins (publicly viewable pins) to be deleted or refused. Wireless names or hardware IDs that have been opted out will cause custom pins (non-public, developer-based pins) to be moved to the next similar ambient signal that is not opted out. The opted-out hardware ID stays unused, but the app developer keeps reliable functionality as required. Note that pins are generally queried only by a wireless device detecting a large number of signals and checking them for a pin type of interest. The infrastructure will adjust custom pins as required to meet the privacy needs of owners while maximizing the usefulness and availability for all wireless device developers. Pins cannot be deleted or purged by anyone other than the wireless name or hardware ID owner, or via system management processes. Finally, once created, pins cannot be edited.

####Data Security for The Developer

Custom pins use complex pin types of up to 255 characters (a hash, for example), serving as the developer’s security token. No one can query pins without explicitly asking for the pin type – and knowing it – first. The longer and more complex a developer's pin type, the more secure it is. Developers may conversely choose to share or make obvious pin types. There are no limits on the number nor variation of pin types you use.

The content data of the pin (payload) should generally be codes or URLs pointing to data in your secure system or to a service such as imgur.  It can be data that only your app will understand. It can be many characters (see limits above), but will likely be short. The system stores linkages only. Actual media content and any other type of content is stored on the developer's secure servers or on those of a selected third-party service. In effect, the Proximal API stores and retrieves linkages between wireless identifiers and content that developers store elsewhere.

Pins are protected differently than what is commonly thought of as online content. Pins are not online content in the standard meaning, but rather triggers, and can only be retrieved with the pin type that a developer used to create them. A pin type that is a 255 character hash is very secure and serves as an API token, but on each individual group of pins a developer creates. Each pin can have entirely separate pin types and multiple pins can hold fragments of a linkage that must be patched together — the developer decides on the security required for the use-case. The Proximal API is aimed to be as fast and flexible as possible, and focused on the wireless name / hardware ID owner as the ultimate controller of all information associated to a wireless identity. Some of these attributes are departures from common web services today.

####Data Security for Wireless Name and Hardware ID Owners

Public pins and all account information is stored on highly secure and redundant cloud services. The system is SSL throughout and all data is encrypted. The wireless name or hardware ID owners have the ability to add or delete any and all data associated to their wireless identifiers at any time.

Any mobile hardware ID (Wi-Fi MAC, Bluetooth MAC, BeaconID, with IMEI, and others) can be registered with The Wireless Registry.

###Other Related Infrastructure

####Email to Wireless Name

Emailing a registered wireless name's owner is possible using the format WirelessName@WirelessRegistry.com. The email is instantly forwarded to the wireless name owner’s registered email, who can then respond directly to the original sender. The registered user remains anonymous and the sender unaware of the recipient’s end-email address — unless the name owner chooses to respond.

Emails can also be sent to hardware IDs through to the registered owner in the same way, following the format AB-12-AB-12-AB-12@WirelessRegistry.com or AB12AB12AB12@WirelessRegistry.com. Use-cases can be built wherein a router of any kind can contact a device or a device’s owner directly and immediately via the wireless ID string, without a direct connection to it.

Although it may be cumbersome, it is similarly possible to email directly to a beacon ID in the same format: E2C56DB5-DFFB-48D2-B060-D0F5A71096E0~00001~00022@WirelessRegistry.com. The email will go through to the registered beacon ID owner’s email address.

####Wireless Name Public URL for public Pins

All wireless strings can have public content associated with them, such as standard pins, visible at www.WirelessRegistry.com/WirelessName or www.WirelessRegistry.com/HardwareID, as determined by the registered owner. 

www.WirelessRegistry.com/WirelessName~HardwareID will take the user directly to the content associated to that particular Wireless Name and hardware ID combination. This also works for beacon IDs in the standard beacon Type 1 format, as well as for all other registerable signals (for example: www.WirelessRegistry.com/E2C56DB5-DFFB-48D2-B060-D0F5A71096E0~00001~00022.)

###Miscelaneous

####Proximity vs. Location

Proximity generally entails one device directly detecting another device. Note that location (lat/long) does not imply that anything else is near a given device, unless an inference – a check-in or some other kind of shared geo-fence attribute – is made to guess or suggest the proximity of other things near that device. Inferring proximity suffers from variations in the quality of the lat/long, movement, or the validity of a check-in. Direct proximal detection of beacons, wireless names, or MAC addresses provides an alternative form of proximal awareness with different attributes than a lat/long based approach. As the number of wireless signals around us grows into the billions, the situation becomes even richer for complex proximity detection and authentication use-cases. For example, meaning can be associated to a complex pattern of signals, rather than just a single signal. The Proximal API enables the development of such use-cases by allowing developers to query and contribute to the meanings of such signals in real-time, even by pattern, group, or change in signal over time.

####Wireless Technology and Spectrum

The Proximal API can apply to signals independently of the technology or spectrum transmitted on. A wireless name can be transmitted on Wi-Fi, Bluetooth, BLE, LTE Direct, or any other technology on any spectrum. Distance and signal strength are likewise disregarded because these are managed by software on the device. An app may check for or to post pins on a given signal based on that signal's type, technology, or strength, all on the device under specific application control. A developer could pin different custom pin types to different types of signals, such as Bluetooth, Wi-Fi, or LTE Direct. The pin’s data payload may, for example, include the signal strength, or any other data of the developer's choice. With these on-board and hardware-specific considerations up to the developer, a multitude of combinations becomes possible.

####Tilde and Spaces

Throughout the Proximal API documentation the use of the tilde “~” character indicates a wireless name (~MyWirelessName) as well as a separator between wireless names and a related hardware ID (MyWirelessName~AB:12:AB:12:AB:12). Users are welcome to choose whether or not to use ~ as the first character in a wireless name. The Proximal API perceives "MyWirelessName” and “~MyWirelessName” as the same. Spaces are likewise ignored in any combination in all wireless names and hardware ID fields.

--

##Resources

###Introduction

The Proximal API is a live public system that all are welcome to use subject to the terms of the API License Agreement. It is designed to be as open and unrestricted as possible for all users and devices. The system responds to spamming in a manner similar to email spam management, such that if a source appears to be a spammer it may be throttled or otherwise managed. 

The Proximal API infrastructure is supported by several top nodes around the world, and nodes are added with increased demand, dynamically (by the system itself) or strategically.

For testing purposes, developers may pin to a range of signals that represent test signals and use test contentTypes of their own selection.

The methods below include Save, Get, and Command; the first Command (Count) is indicated below.

Pins cannot be edited and can be deleted only via the action of the wireless name or hardware ID owner. Pins do not expire but are created and retrieved via pin creation date/time parameters.

###API Entry Points

**Action** | **Method** | **Entry Point**
---------- | -----------| --------------
**Save pins** | POST | _https://api.wirelessregistry.com/v1/pins_
**Get pins** | GET | _https://api.wirelessregistry.com/v1/pins_

###Save Pins
**A. Parameters**

**PARAMETER** | **REQUIRED / OPTIONAL** | **Type** | **VALUE** | ** DESCRIPTION**
------|-----|------| ------ | ------ 
**devices** | required | _array_ | one or more valid **wirelessName** and **hardwareID** pairs | The set of identifiers for the devices where the content must be pinned.
**devices → wirelessName** | required / optional (see note below) | _string_ | valid wireless name | Wireless name where the pin should be added.
**devices → hardwareID** | required / optional (see note below) | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device where the pin must be added.
**listenerID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the wireless adapter used to detect the ambient wireless signals used in the API call. If more than one, then that most important for the use-case. Field required for future functions, but the developer can enter any valid hardware ID if the actual hardware ID is not available.
**AdID** | optional | _string_ | see grammar below | Valid mobile advertisement identifier.
**type** | required | _string_ | valid standard or custom pin type (max 255 characters) | Type of the pin being added.
**data** | required | _text_ | max 65K chars | The content added, depending on the type used.
**label** | optional | _text_ | max 255 chars, empty string by default | Unstructured field for tagging, captioning, labeling, or otherwise describing the pin's content.

> **Note:** If the pin type is a standard one, the **hardwareID** in a pair becomes optional. If the pin type is a custom one, either the **wirelessName** or the **hardwareID** in a pair can be missing, as long as they are not both missing at the same time.

> **Note:** If the pin type is set to _generateType_, the API endpoint will generate the type as a 44 random characters string. This value is returned in the response as **generated_pinType**.

> **AdID Grammar:** <br/>
> **AdID** ::= Type + "^" + Value <br/>
> **Type** ::= "ios_ifa" | "google_aid" | "windows_aid" <br/>
> **Value** ::= device's AdID

**B. Response**

**Fatal error:**
PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _string_ | Short description of the fatal error.

**Success:**
PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**success** | _array_ of _string_| Each element has a confirmation message, specifying which (**wirelessName**, **hardwareID**) pair was processed successfully.

**Mixed results:**
PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _array_ of _string_ | Each element has an error message, specifying which (**wirelessName**, **hardwareID**) pair caused the error, as well as details about the nature of the error.
**success** | _array_ of _string_ | Each element has a confirmation message, specifying which (**wirelessName**, **hardwareID**) pair was processed successfully.

**C. EXAMPLES**

**Generic valid data structure**

    [devices] => Array
        (
            [0] => Array
                (
                    [wirelessName] => 'wn 1'
                    [hardwareID] => '6E:AA:40:F4:8F:DA'
                )

            [1] => Array
                (
                    [wirelessName] => 'wn 2'
                    [hardwareID] => 'D8:16:13:AB:28:AD'
                )

        )
    [listenerID] => 'B1:C2:FC:D9:CD:10'
    [type] => 'image'
    [data] => 'https://wirelessregistry.com/assets/img/default-pin.png'
	[AdID] => 'ios_ifa^AAAAAAAAA-BBBB-CCCC-1111-222222220000




Each API method has two entry points, depending on the purpose of use. One, on testing servers, is used for testing and development. The second one, on the production servers, is to be used only on the applications released to the application stores. The methods include POST, GET, and COUNT; pins cannot be edited and pins are only deleted via the action of the wireless name or hardware ID owner. Pins do not expire.

**Testing Server**: Testing servers allow developers to use the API in any way without the pins showing up in the live system. All pins are purged after 60 minutes.

**Production Server**: The live system where public pins show up on public pinboards, wireless name owner accounts, and other live systems. Custom pins are still as private to the developer as the developers careful usage of the custom pin type.
   
###1. POST v1/pins

SERVER TYPE | URL
----------- | ---------------
**testing** | http://testapi.wirelessregistry.com/v1/pins
**production** | https://api.wirelessregistry.com/v1/pins


###2. GET v1/pins

SERVER TYPE | URL
----------- | ---------------
**testing** | http://testapi.wirelessregistry.com/v1/pins
**production** | https://api.wirelessregistry.com/v1/pins


###3. GET v1/pins/count

SERVER TYPE | URL
----------- | ---------------
**testing** | http://testapi.wirelessregistry.com/v1/pins/count
**production** | https://api.wirelessregistry.com/v1/pins/count


---


##1. POST v1/pins

###A. Parameters

PARAMETER | REQUIRED/OPTIONAL | TYPE(s) | VALUE(s) | DESCRIPTION
--------- | ----------------- | ------- | -------- | -----------
**devices** | required | _array_ | one or more valid **wirelessName** and **hardwareID** pairs | The set of identifiers for the devices where the content must be pinned
**wirelessName** | required | _string_ | valid Wireless Name | Wireless Name where the pin should be added
**hardwareID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device where the pin must be added
**listenerID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device's network interface card used to send the API call
**AdID** | optional | _string_ | see grammar below | The pseduo-random bitstring associated with Android, iOS and Windows phones |
**type** | required | _string_ | valid standard or custom pin type | Type of the pin being added
**data** | required | _text_ | Max 65K chars | This is the content added, depending on the type used
**label** | optional | _string_ | Max 255 chars open, empty string by default | Unstructured field for tagging, captioning, labeling or otherwise describing the pin's content

> **Note:** If the pin type is a standard one, the **hardwareID** in a pair becomes optional. If the pin type is a custom one, either the **wirelessName** or the **hardwareID** in a pair can be missing, as long as they are not both missing at the same time.

> **AdID Grammar:** <br/>
> **AdID** ::= Type + "^" + Value <br/>
> **Type** ::= "ios_ifa" | "google_aid" | "windows_aid" <br/>
> **Value** ::= device's AdID


###B. RESPONSE
  
**Fatal Error:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _string_ | short description of the fatal error

**Success:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**success** | _array_ of _string_| each element has a confirmation message, specifying which (**wirelessName**, **hardwareID**) pair was processed successfully

**Mixed results:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _array_ of _string_ | each element has an error message, specifying which (**wirelessName**, **hardwareID**) pair caused the error, as well as details about the nature of the error
**success** | _array_ of _string_ | each element has a confirmation message, specifying which (**wirelessName**, **hardwareID**) pair was processed successfully


###C. EXAMPLES

**Generic valid data structure**

    [devices] => Array
        (
            [0] => Array
                (
                    [wirelessName] => 'wn 1'
                    [hardwareID] => '6E:AA:40:F4:8F:DA'
                )

            [1] => Array
                (
                    [wirelessName] => 'wn 2'
                    [hardwareID] => 'D8:16:13:AB:28:AD'
                )

        )
    [listenerID] => 'B1:C2:FC:D9:CD:10'
    [type] => 'image'
    [data] => 'https://wirelessregistry.com/assets/img/default-pin.png'
	[AdID] => 'ios_ifa^AAAAAAAAA-BBBB-CCCC-1111-222222220000

---

##2. GET v1/pins

###A. Parameters

PARAMETER | REQUIRED/OPTIONAL | TYPE(s) | VALUE(s) | DESCRIPTION
--------- | ----------------- | ------- | -------- | -----------
**wirelessNames** | required | _array_ of _string_ | valid Wireless Name | Wireless Names from where to retrieve the pins
**hardwareIDs** | required | _array_ of _string_ | valid MAC address or IMEI identifier | Hardware IDs of the devices from where to retrieve the pins
**listenerID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device's network interface card used to send the API call
**AdID** | optional | _string_ | see grammar above | the pseduo-random bitstring associated with Android, iOS and Windows phones |
**types** | required | _array_ of _string_ | valid standard or custom pin type | Pin types requested
**startDate** | optional | _string_ | String-formatted date on the pattern "MM/DD/YYYY hh:mm:ss" (month/day/year hours:minutes:seconds) | The beginning of the time interval that will limit the request
**endDate** | optional | _string_ | String-formatted date on the pattern "MM/DD/YYYY hh:mm:ss" (month/day/year hours:minutes:seconds) | The end of the time interval that will limit the request

> **Note:** The default time value for **startDate** is 00:00:00. The default time value for **endDate** is 23:59:59


###B. RESPONSE

**Fatal Error:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _string_ | short description of the fatal error

**Success:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**result** | JSON _array_ | Contains two distinct elements: **meta** and **pins**
**meta** | JSON _array_ | Contains metainformation about the result
**pins** | JSON _array_ | Contains the pins retrieved by the request


    {
        "meta": {
            "count": 5
        },
        "pins": [
            {
                "wirelessName": "wn 1",
                "data": "https://wirelessregistry.com/assets/img/default-pin.png",
                "label": "label test",
                "type": "image",
                "addingDate": '02/15/2014 00:00:00'
            },
            {
                "wirelessName": "E2C56DB5-DFFB-48D2-B060-D0F5A71096E0~00000~00000",
                "data": "data test1",
                "label": "",
                "type": "text",
                "addingDate": '02/15/2014 00:00:00'
            },
            {
                "wirelessName": "wn 1",
                "data": "data test",
                "label": "label test",
                "type": "custom-type-label-of-my-own-design",
                "addingDate": '02/17/2014 00:00:00'
            },
            {
                "hardwareID": "6E:AA:40:F4:8F:DA",
                "data": "https://wirelessregistry.com/assets/img/default-pin.png",
                "label": "",
                "type": "image",
                "addingDate": '02/15/2014 00:00:00'
            },
            {
                "hardwareID": "6E:AA:40:F4:8F:DA",
                "data": "https://wirelessregistry.com/assets/img/default-pin.png",
                "label": "",
                "type": "image",
                "addingDate": '02/25/2014 00:00:00'
            }
        ]
    }

> **Note:** 'addingDate' field is formatted based on the following pattern: MM/DD/YYYY hh:mm:ss (month/day/year hours:minutes:seconds)

**Mixed results:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _array_ of _string_ | each element has an error message, specifying which **wirelessName** or **hardwareID** caused the error, as well as the nature of that error
**success** | JSON _array_ | **meta** and **pins** retrieved for the valid request parameters


###C. EXAMPLES

**Generic valid data structure**

    [wirelessNames] => Array
        (
            [0] => 'wn 1'
            [1] => 'wn 2'
        )
    [hardwareIDs] => Array
        (
            [0] => '6E:AA:40:F4:8F:DA'
            [1] => 'D8:16:13:AB:28:AD'
        )
    [types] => Array
        (
            [0] => 'image'
            [1] => 'custom-type-label-of-my-own-design'
        )
    [listenerID] => 'B1:C2:FC:D9:CD:10'
    [startDate] => '01/01/2014 00:00:00'
    [endDate] => '01/31/2014 00:00:00'



---

##3. GET v1/pins?count

###A. Parameters

PARAMETER | REQUIRED/OPTIONAL | TYPE(s) | VALUE(s) | DESCRIPTION
--------- | ----------------- | ------- | -------- | -----------
**wirelessNames** | required | _array_ of _string_ | valid Wireless Name | Wireless Names from where to retrieve the pins
**hardwareIDs** | required | _array_ of _string_ | valid MAC address or IMEI identifier | Hardware IDs of the devices from where to retrieve the pins
**listenerID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device's network interface card used to send the API call
**types** | required | _array_ of _string_ | valid standard or custom pin type | Pin types requested
**startDate** | optional | _string_ | String-formatted date on the pattern "MM/DD/YYYY hh:mm:ss" (month/day/year hours:minutes:seconds) | The beginning of the time interval that will limit the request
**endDate** | optional | _string_ | String-formatted date on the pattern "MM/DD/YYYY hh:mm:ss" (month/day/year hours:minutes:seconds) | The end of the time interval that will limit the request

> **Note:** The default time value for **startDate** is 00:00:00. The default time value for **endDate** is 23:59:59


###B. RESPONSE

**Fatal Error:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _string_ | short description of the fatal error


**Success:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**result** | JSON _array_ | Contains two distinct elements: **meta** and **pins**
**meta** | JSON _array_ | Contains metainformation about the result
**pins** | JSON _array_ | Contains the count of pins retrieved by the request, for each valid **wirelessName** or **hardwareID**. Each pin type is counted in a separate entry.


    {
        "meta": {
            "count": 6
        },
        "pins": [
            {
                "wirelessName": "test",
                "count": 0
            },
            {
                "wirelessName": "myotherrideisatitan",
                "count": 0
            },
            {
                "hardwareID": "6E:AA:40:F4:8F:DA",
                "type": "image",
                "count": 2
            },
            {
                "hardwareID": "6E:AA:40:F4:8F:DA",
                "type": "text",
                "count": 1
            },
            {
                "hardwareID": "D8:16:1A:B2:8C:AD",
                "type": "image",
                "count": 2
            },
            {
                "hardwareID": "D8:16:1A:B2:8C:AD",
                "type": "text",
                "count": 1
            }
        ]
    }

**Mixed results:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _array_ of _string_ | each element has an error message, specifying which **wirelessName** or **hardwareID** caused the error, as well as the nature of that error
**success** | JSON _array_ | **meta** and **pins** retrieved for the valid request parameters


###C. EXAMPLES

**Generic valid data structure**

    [wirelessNames] => Array
        (
            [0] => 'wn 1'
            [1] => 'wn 2'
        )
    [hardwareIDs] => Array
        (
            [0] => '6E:AA:40:F4:8F:DA'
            [1] => 'D8:16:13:AB:28:AD'
        )
    [types] => Array
        (
            [0] => 'image'
            [1] => 'custom-type-label-of-my-own-design'
        )
    [listenerID] => 'B1:C2:FC:D9:CD:10'
    [startDate] => '01/01/2014 00:00:00'
    [endDate] => '01/31/2014 00:00:00'
