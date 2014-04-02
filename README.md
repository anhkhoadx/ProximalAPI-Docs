#Proximal API v2.0

##Introduction

###Definitions

The Wireless Registry Proximal API allows the association of content to wireless ID strings and the subsequent retrieval of this content. Wireless devices generally detect Wireless Names and Hardware IDs around them in a range of combinations. These signals vary from Wi-Fi Names, Bluetooth names, and MAC addresses, to iBeacon IDs and a number of similar wireless expressions and IDs to come via new technologies and standards. The Proximal API outlined here is the first open API that allows any device to both create and retrieve associations to any signal, while at the same time respecting an industry approved opt-out mechanism, and enabling the full control of associated content by the registered owners of the signals involved. 
   
The Proximal API makes use of several concepts, that are defined below.
  
####1. Wireless Name

a) **Wi-Fi and Bluetooth Names**
 
A Wireless Name is a word or phrase transmitted from a Wireless Device as an ID string or form of device or network identification. Currently the Proximal API responds to one to thirty-two characters (32 bytes) in length that typically corresponds to the SSID (Service Set Identifier) of a Wi-Fi or Bluetooth device. SSIDs are often referred to as “network names” and are broadcast by a device to all receiving devices within the broadcast radius of a device’s networking hardware.
 
A new device typically has an SSID that is set by default by the device manufacturer. This SSID can be manually changed on a number of devices, such as smartphones, tablets, laptops, PCs and wireless network routers in the home or office.

b) **iBeacon and BLE Names**
 
The API will respond to BLE or Bluetooth Smart identifiers. The first set of identifiers included is a special type of Wireless Name called iBeacon. iBeacon is the Apple Trademark for an indoor positioning system that Apple Inc. calls "a new class of low-powered, low-cost transmitters that can notify nearby iOS 7 devices of their presence." They can also be used, in a limited manner, by the Android operating system. The technology enables an iOS device or other hardware to send push notifications to iOS devices in close proximity.

The accepted format for an iBeacon Wireless Name is to split it in groups of digits according to the formula: 8-4-4-12~5~5. All groups are hexadecimal, with the exception of the last two groups of 5 decimal digits. These two groups are usually called the Major and Minor values, in that order, and take values between 00000 and 65535.

    Example of an iBeacon Wireless Name:

    E2C56DB5-DFFB-48D2-B060-D0F5A71096E0~00000~00000

See http://en.wikipedia.org/wiki/IBeacon for more details about iBeacon.

####2. Hardware ID

Our system supports at this moment two main types of Hardware IDs:

a) **MAC address**

The most common Hardware ID used by our system is the MAC address. A **media access control address** (**MAC address**) is a unique identifier assigned to network interfaces for communications on the physical network segment. MAC addresses are used as a network address for most IEEE 802 network technologies, including Ethernet; and in the case of Wi-Fi and Bluetooth devices, this MAC address is transmitted around the device to identify it to other devices in the immediate area.
  
There are many ways of writing a MAC address. For ease of reading, our system converts all valid MAC addresses to what we call _the normalized version_. This is a variant of the standard IEEE 802, with six groups of capitalized hexadecimal digits, separated by colons (:) in transmission order.

    A normalized MAC address:

    01:23:45:67:89:AB

We also accept other formats as well, although they are all converted to the normalized version:

    Other accepted MAC address formats:

    01:23:45:67:89:ab
    01-23-45-67-89-ab
    0123456789ab
    0123.4567.89ab

See http://en.wikipedia.org/wiki/MAC_address for more details about MAC addresses.

b) **IMEI**

The International Mobile Station Equipment Identity or IMEI is a number, usually unique, to identify most mobile phones (i.e., GSM, UMTS, LTE and iDEN), as well as some satellite phones. It is usually found printed inside the battery compartment of the phone, but can also be displayed on-screen on most phones by entering *#06# on the dialpad, or alongside other system information in the settings menu on smartphone operating systems.

As of 2004, the format of the IMEI is AA-BBBBBB-CCCCCC-D, where all the digits are decimal. We, however use a slightly different version, replacing the "-" separator with "~".

    AA~BBBBBB~CCCCCC~D

See http://en.wikipedia.org/wiki/IMEI for more details about IMEI.

####3. Pins

A pin is an information token that is attached to a Wireless Name or a Hardware ID, or a combination of both Wireless Name and Hardware ID. Pins are the basic unit that is accepted by the API. Pins are text strings from 1-65k characters and while standard pin types expect linkages to the matching type of content for that pin type, custom pins can hold any combination codes and information that a developer would like to use. A wide range of use cases is possible.

Some developers pin codes that represent content on their servers so that any instance of their application can check surrounding detectable signals and retrieve those codes left by other instances of their app on the same signals -  providing app to app communication without GPS or check-ins. 
 
Some developers attach lists of wireless identifiers of one type to wireless identifiers of another type - so the detection of a Wi-Fi signal might reveal a list of NFC codes in a room pinned by another device which detected both.

#####Pin Security and Treatment

The API respects the World's first industry accepted proximal signal privacy and opt-out system which is managed by the Future of Privacy Forum in Washington, DC. Mobile detection data analytics companies from around the world are part of this system which protects the privacy of individuals who register their proximal signals. Developers using the Proximal API are **automatically covered by this industry leading privacy best practice**. Please see www.futureofprivacy.org for more detailed information.
 
The API is also the first proximal API to be integrated into The Wireless Registry Inc. system of Wireless Name and ID registration. This global system allows individuals and businesses to register wireless names and ID strings they own and that represent them. The API **respects the content the owners proactively manage** and respects their privacy settings throughout.
 
The proximal API is un-metered and free. The system is supported via an Wireless Registry ownership model rather than an API usage-based model. Standard pins are secured via the wireless name owner having full control of all standard pins regardless of their source. Custom pins are secured via each developer using complex and secure pin types that they they control the management of.
  
#####Pin types

Our system supports two main categories of pins: **standard pins** and **custom pins**.

a) **Standard Pins**

Standard pin types are defined by The Wireless Registry, with clear rules and restrictions for each standard type. They are ALWAYS visible on our portal (https://reg.wirelessregistry.com). Therefore they are not well suited for private information.

At this moment the system supports the following standard types:

PIN TYPE | DATA TYPE | DATA CONTENT VALUE(s) | DESCRIPTION
-------- | --------- | -------- | -----------
**image** | _string_ | max 255 chars | The path to an image file. Usually hosted on imgur.com, although any other server or image hosting service can be used.
**text** | _text_ | max 65K chars | A generic textual message.
**url** | _string_ | max 255 chars | A generic URL path.
**audio** | _string_ | max 255 chars | A URL path to a streaming media resource: audio, video, pages from YouTube, Vimeo, etc.

> **Note:** The **audio** pin type is scheduled to be changed to **streamingmedia**

Further standard types are also scheduled to be added in the near future. Here is a preview for a few of them:

- facebook
- twitter
- pinterest
- linkedin
- email
- phone

...and many more.

Standard pins must be created on a single Wireless Name or Wireless Name ~ Hardware ID combination at a time. An example of a standard pin would be pining a picture to the Wireless Name of a restaurant. Any app on any device can check the open API for content associated with the Wireless Name of the restaurant and will get the pin immediately and could render the picture. 

It is important to note that the API can also be queried with no pin type parameter specified. In this case the API will respond with ALL standard pins associated to the Wireless Name checked, but only standard pins.

b) **Custom Pins**

In addition to the standard pin types, we also allow custom pin types to be set up by the API users. They are NEVER displayed on our portal and can only be displayed in third party applications, via the API. Custom pin types have only one restriction: **their length must be between 25 and 255 characters**. No custom types with less than 25 characters are permitted, as we reserved that space for further expansion of the standard types.

Custom pin types are defined by the API user and these pins cannot be retrieved via the API unless the pin type is included correctly in the query. In this way, custom pins can be kept private with pin types that are long hashes kept known only to the developer, or you can share your custom pin types if you want others to have access to your pins.
 
Custom pins can be created on an array of 1 to 10 Wireless Name, Wireless Name ~ Hardware ID, or Hardware ID alone combinations at a time. An example of a custom pin would be an application pinning a message or user ID to the top 5 strongest MAC address signals in a room. In this case other installs of that same app can retrieve those pins with the app specific custom pin type simply by checking all detected MACs against the API and the correct custom pin type known only to that app.

Note that unlike standard pins, custom pins can never be retrieved without being explicitly requested in the query. The requester must know the custom pin type and query for that type. There are no pin type parameter ranges or wildcards at this time.

**Pin Use Combinations**
 
When custom pins are associated with both stationary signals such as Wi-Fi access points or ibeacons, as well as to the signals of moving devices such as MAC addresses and iPhone-based ibeacons, a wide range of new contextual awareness and device-to-device sharing of pin data is possible.

Creative uses of pins allow 2 mobile app installs to deduce the are immediately proximal via detecting the same 2 or 3 ambient signals - quickly and without the need for GPS check-ins. Other applications pin custom triggers such as game tokens to ambient signals that persist for days or months that other running apps detect when checking ambient signals. Still others pin usernames or statistics so other devices can see how many users are or have been in a location over a defined period.

The API works in-flight with GoGo In-Flight, on moving buses and cars, and anywhere a data connection is available - completely GPS, battery drain, and check-in free. The API will continue to expand the list of supported Wireless Name and Hardware ID formats, adding Zigbee IDs in 2014 and LTE Direct Expressions in 2015.
     
  
---

##Entry Points

Each API method has two entry points, depending on the purpose of use. One, on staging servers, is used for testing and development. The second one, on the production servers, is to be used only on the applications released to the application stores. The production servers will be available April 12th, 2014.
  
###1. POST v2/wns/pins

SERVER TYPE | URL
----------- | ---------------
**staging** | http://stagingapi.wirelessregistry.com/api/v2/wns/pins
**production** | https://api.wirelessregistry.com/api/v2/wns/pins


###2. GET v2/wns/pins

SERVER TYPE | URL
----------- | ---------------
**staging** | http://stagingapi.wirelessregistry.com/api/v2/wns/pins
**production** | https://api.wirelessregistry.com/api/v2/wns/pins


###3. GET v2/wns/pins?count

SERVER TYPE | URL
----------- | ---------------
**staging** | http://stagingapi.wirelessregistry.com/api/v2/wns/pins?count
**production** | https://api.wirelessregistry.com/api/v2/wns/pins?count


---


##1. POST v2/wns/pins

###A. Parameters

PARAMETER | REQUIRED/OPTIONAL | TYPE(s) | VALUE(s) | DESCRIPTION
--------- | ----------------- | ------- | -------- | -----------
**devices** | required | _array_ | one or more valid **wirelessName** and **hardwareID** pairs | The set of identifiers for the devices where the content must be pinned
**wirelessName** | required | _string_ | valid Wireless Name | Wireless Name where the pin should be added
**hardwareID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device where the pin must be added
**listenerID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device's network interface card used to send the API call
**type** | required | _string_ | valid standard or custom pin type | Type of the pin being added
**data** | required | _text_ | Max 65K chars | This is the content added, depending on the type used
**label** | optional | _string_ | Max 255 chars open, empty string by default | Unstructured field for tagging, captioning, labeling or otherwise describing the pin's content

> **Note:** If the pin type is a standard one, the **hardwareID** in a pair becomes optional. If the pin type is a custom one, either the **wirelessName** or the **hardwareID** in a pair can be missing, as long as they are not both missing at the same time.


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
    [data] => 'https://reg.wirelessregistry.com/assets/img/default-pin.png'

---

##2. GET v2/wns/pins

###A. Parameters

PARAMETER | REQUIRED/OPTIONAL | TYPE(s) | VALUE(s) | DESCRIPTION
--------- | ----------------- | ------- | -------- | -----------
**wirelessNames** | required | _array_ of _string_ | valid Wireless Name | Wireless Names from where to retrieve the pins
**hardwareIDs** | required | _array_ of _string_ | valid MAC address or IMEI identifier | Hardware IDs of the devices from where to retrieve the pins
**listenerID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device's network interface card used to send the API call
**types** | required | _array_ of _string_ | valid standard or custom pin type | Pin types requested
**startDate** | optional | _string_ | String-formatted date on the pattern "MM/DD/YYYY" | The beginning of the time interval that will limit the request
**endDate** | optional | _string_ | String-formatted date on the pattern "MM/DD/YYYY" | The end of the time interval that will limit the request


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
                "data": "https://reg.wirelessregistry.com/assets/img/default-pin.png",
                "label": "label test",
                "type": "image",
                "addingDate": '02/15/2014'
            },
            {
                "wirelessName": "E2C56DB5-DFFB-48D2-B060-D0F5A71096E0~00000~00000",
                "data": "data test1",
                "label": "",
                "type": "text",
                "addingDate": '02/15/2014'
            },
            {
                "wirelessName": "wn 1",
                "data": "data test",
                "label": "label test",
                "type": "custom-type-label-of-my-own-design",
                "addingDate": '02/17/2014'
            },
            {
                "hardwareID": "6E:AA:40:F4:8F:DA",
                "data": "https://reg.wirelessregistry.com/assets/img/default-pin.png",
                "label": "",
                "type": "image",
                "addingDate": '02/15/2014'
            },
            {
                "hardwareID": "6E:AA:40:F4:8F:DA",
                "data": "https://reg.wirelessregistry.com/assets/img/default-pin.png",
                "label": "",
                "type": "image",
                "addingDate": '02/25/2014'
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
    [startDate] => '01/01/2014'
    [endDate] => '01/31/2014'



---

##3. GET v2/wns/pins?count

###A. Parameters

PARAMETER | REQUIRED/OPTIONAL | TYPE(s) | VALUE(s) | DESCRIPTION
--------- | ----------------- | ------- | -------- | -----------
**wirelessNames** | required | _array_ of _string_ | valid Wireless Name | Wireless Names from where to retrieve the pins
**hardwareIDs** | required | _array_ of _string_ | valid MAC address or IMEI identifier | Hardware IDs of the devices from where to retrieve the pins
**listenerID** | required | _string_ | valid MAC address or IMEI identifier | Hardware ID of the device's network interface card used to send the API call
**types** | required | _array_ of _string_ | valid standard or custom pin type | Pin types requested
**startDate** | optional | _string_ | String-formatted date on the pattern "MM/DD/YYYY" | The beginning of the time interval that will limit the request
**endDate** | optional | _string_ | String-formatted date on the pattern "MM/DD/YYYY" | The end of the time interval that will limit the request


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
    [startDate] => '01/01/2014'
    [endDate] => '01/31/2014'
