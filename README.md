#Proximal API v2.0

##Introduction

###Definitions

The Proximal API makes use of several concepts, that are defined below.

####1. Wireless Name

A wireless name is a word or phrase from one to thirty-two characters in length that typically corresponds to the SSID (Service Set Identifier) of your device. SSIDs are often referred to as “network names” and are broadcast by your device to all receiving devices within the broadcast radius of your device’s networking hardware.

A new device typically has an SSID that is set by default by the device manufacturer. This SSID can be manually changed on a number of devices, such as smartphones, tablets, laptops, PCs and wireless network routers in the home or office.

####2. Hardware Id

Our system supports at this moment three type of harwareIds:

a) **MAC address**

The most common harwareId used by our system is the MAC address. A **media access control address** (**MAC address**) is a unique identifier assigned to network interfaces for communications on the physical network segment. MAC addresses are used as a network address for most IEEE 802 network technologies, including Ethernet.

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

b) **iBeacon**

iBeacon is the Apple Trademark for an indoor positioning system that Apple Inc. calls "a new class of low-powered, low-cost transmitters that can notify nearby iOS 7 devices of their presence." They can also be used, in a limited manner, by the Android operating system. The technology enables an iOS device or other hardware to send push notifications to iOS devices in close proximity.

The accepted format for an iBeacon hardwareId is to split it in groups of digits according to the formula: 8-4-4-12~5~5. All groups are hexadecimal, with the exception of the last two groups of 5 decimal digits. These two groups take values between 00000 and 65535.

    Example of an iBeacon harwareId:

    E2C56DB5-DffB-48D2-B060-D0F5A71096E0~00000~00000

See http://en.wikipedia.org/wiki/IBeacon for more details about iBeacon.

c) **IMEI**

The International Mobile Station Equipment Identity or IMEI is a number, usually unique, to identify most mobile phones (i.e., GSM, UMTS, LTE and iDEN), as well as some satellite phones. It is usually found printed inside the battery compartment of the phone, but can also be displayed on-screen on most phones by entering *#06# on the dialpad, or alongside other system information in the settings menu on smartphone operating systems.

As of 2004, the format of the IMEI is AA-BBBBBB-CCCCCC-D, where all the digits are decimal. We, however use a slightly different version, replacing the "-" separator with "~".

    AA~BBBBBB~CCCCCC~D

See http://en.wikipedia.org/wiki/IMEI for more details about IMEI.

####3. Pins

A pin is an information token that is attached to a Wireless Name or a Hardware Id

#####Pin types

Our system supports two main categories of pins: **standard pins** and **custom pins**.

a) **Standard Pins**

Standard pin types are defined by The Wireless Registry, with clear there are rules and restrictions for each standard type. They are ALWAYS visible on our portal (https://reg.wirelessregistry.com). Therefore they are not well suited for private information.

At this moment the system supports the following standard types:

PIN TYPE | DATA TYPE | VALUE(s) | DESCRIPTION
-------- | --------- | -------- | -----------
**image** | _string_ | max 255 chars | The path to an image file. Usually hosted on imgur.com, although any other server or image hosting service can be used.
**text** | _text_ | max 65K chars | A generic textual message
**url** | _string_ | max 255 chars | A generic URL path
**audio** | _string_ | max 255 chars | A URL path to a streaming media resource: audio, video, pages from YouTube, Vimeo, etc.

> **Note:** The **audio** pin type is scheduled to be changed to **streamingMedia**

Further standard types are also scheduled to be added in the near future. Here is a preview for a few of them:

- facebook
- twitter
- pinterest
- linkedin
- email
- phone

...and many more.


**Custom Pins**

In addition to the standard pin types, we also allow custom pin types to be set up by the API users. They are NEVER displayed on our portal and can only be displayed in third party applications, via the API. Custom pin types have only one restriction: **a minimum length of 25 characters**. No custom types with less than 25 characters are permitted, as we reserved that space for further expansion of the standard types.

---

##Entry Points

1. POST v2/wns/pins - http://stagingapi.wirelessregistry.com/api/v2/wns/pins
2. GET v2/wns/pins - http://stagingapi.wirelessregistry.com/api/v2/wns/pins

---


##1. POST v2/wns/pins

###A. Parameters

PARAMETER | REQUIRED/OPTIONAL | TYPE(s) | VALUE(s) | DESCRIPTION
--------- | ----------------- | ------- | -------- | -----------
**devices** | required | _array_ | one or more valid **wirelessName** and **hardwareId** pairs | The set of identifiers for the devices where the content must be pinned
**wirelessName** | required | _string_ | valid Wireless Name | Wireless Name where the pin should be added
**hardwareId** | required | _string_ | valid MAC or iBeacon addresses or IMEI identifier | Hardware ID of the device where the pin must be added
**listenerId** | required | _string_ | valid MAC or iBeacon addresses or IMEI identifier | Hardware ID of the device's network interface card used to send the API call
**type** | required | _string_ | valid standard or custom pin type | Type of the pin being added
**data** | required | _text_ | Max 65K chars | This is the content added, depending on the type used
**label** | optional | _string_ | Max 255 chars open, empty string by default | Unstructured field for tagging, captioning, labeling or otherwise describing the pin's content


###B. RESPONSE
  
**Fatal Error:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _string_ | short description of the fatal error

**Success:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**success** | _array_ of _string_| each element has a confirmation message, specifying which (**hardwareId**, **wirelessName**) pair was processed successfully

**Mixed results:**

PARAMETER | TYPE(s)  | DESCRIPTION
--------- | -------- | -----------
**error** | _array_ of _string_ | each element has an error message, specifying which (**hardwareId**, **wirelessName**) pair caused the error, as well as details about the nature of the error
**success** | _array_ of _string_ | each element has a confirmation message, specifying which (**hardwareId**, **wirelessName**) pair was processed successfully


###C. EXAMPLES

**Generic valid data structure**

    [devices] => Array
        (
            [0] => Array
                (
                    [wirelessName] => 'wn 1'
                    [hardwareId] => '6E:AA:40:F4:8F:DA'
                )

            [1] => Array
                (
                    [wirelessName] => 'wn 2'
                    [hardwareId] => 'D8:16:13:AB:28:AD'
                )

        )
    [listenerId] => 'B1:C2:FC:D9:CD:10'
    [type] => 'image'
    [data] => 'https://reg.wirelessregistry.com/assets/img/default-pin.png'

---

##2. GET v2/wns/pins

###A. Parameters

PARAMETER | REQUIRED/OPTIONAL | TYPE(s) | VALUE(s) | DESCRIPTION
--------- | ----------------- | ------- | -------- | -----------
**wirelessNames** | required | _array_ of _string_ | valid Wireless Name | Wireless Names from where to retrieve the pins
**hardwareIds** | required | _array_ of _string_ | valid MAC or iBeacon addresses or IMEI identifier | Hardware IDs of the devices from where to retrieve the pins
**listenerId** | required | _string_ | valid MAC or iBeacon addresses or IMEI identifier | Hardware ID of the device's network interface card used to send the API call
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
                "wirelessName": "wn 1",
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
                "hardwareId": "6E:AA:40:F4:8F:DA",
                "data": "https://reg.wirelessregistry.com/assets/img/default-pin.png",
                "label": "",
                "type": "image",
                "addingDate": '02/15/2014'
            },
            {
                "hardwareId": "6E:AA:40:F4:8F:DA",
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
**error** | _array_ of _string_ | each element has an error message, specifying which **hardwareId** or **wirelessName** caused the error, as well as the nature of that error
**success** | JSON array | **meta** and **pins** retrieved for the valid request parameters


###C. EXAMPLES

**Generic valid data structure**

    [wirelessNames] => Array
        (
            [0] => 'wn 1'
            [1] => 'wn 2'
        )
    [hardwareIds] => Array
        (
            [0] => '6E:AA:40:F4:8F:DA'
            [1] => 'D8:16:13:AB:28:AD'
        )
    [types] => Array
        (
            [0] => 'image'
            [1] => 'custom-type-label-of-my-own-design'
        )
    [listenerId] => 'B1:C2:FC:D9:CD:10'
    [startDate] => '01/01/2014'
    [endDate] => '01/31/2014'
