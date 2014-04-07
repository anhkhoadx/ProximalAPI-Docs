##Proximal API v2.0 - Additional Notes

###Email to a Wireless Name

Emailing to a wireless name is possible using the format WirelessName@WirelessRegistry.com or HardwareID@WirelessRegistry.com. The email will enter the system and be forwarded immediately to the Wireless Name owner who can then respond directly to the original sender. Emails can also be sent to a Hardware ID in the same manner, for example AB-12-AB-12-AB-12@wirelessregistry.com or AB12AB12AB12@wirelessregistry.com and flow through to the registered owner. Innovative use cases can be built where a router of any kind can contact a device or the owner of the device directly via the wireless ID string without a direct connection to it.
  
###Wireless Name Public URL for public Pins

All wireless strings may have public content associated with them and this content can be seen at www.WirelessRegistry.com/WirelessName or www.WirelessRegistry.com/HardwareID. This page shows all public content, such as standard pins, that is associated to the wireless string and allowed by the registered owner. www.WirelessRegistry.com/WirelessName~HardwareID will take the user directly to the content associated to that particular wireless name and hardwareID combination.
 
###Wireless Technology and Spectrum

Note that the wireless signals in question are independent of the technology or spectrum they are transmitted on. A wireless name can be transmitted on Wi-Fi, Bluetooth, BLE, LTE-Direct or any other technology on any spectrum. Distance and signal strength are also not included as these are managed on device by your software. You may choose to check a wireless signal for pins or to pin to a wireless signal based on the type of signal or based on a signal strength. This is all done on device under specific application control. You may pin different custom pin types for different types of signals - for Bluetooth, or Wi-Fi, or LTE-Direct for example. You may include the signal strength or any other data you wish in the data payload of the pin. This is all up to the developer and the combinations allow for creative implementations.
       
###Tilde

Throughout the documentation and in recommended use-cases you will note the use of the tilde "~". This character will be used as an indicator of a wireless name (~MyWirelessName) as well as a separator between wireless names and a related hardware ID (MyWirelessName~AB:12:AB:12:AB:12).
 
###Pin Ownership, Overall Data Ownership

The Wireless Registry considers all data in the system to be owned and controlled by the registered wireless string owners. This means registrants of a wireless name control all pins at all times. HardwareID registrants similarly control all pins, both Standard pins and Custom pins. Developers can freely add pins to any wireless signal at no cost and also query the system without restriction or cost - and the Registry and API infrastructure of The Wireless Registry will automatically ensure the pins respect the privacy settings and control requests of all Wireless Name and Hardware ID owners. 

Wireless Names or hardware IDs that have been opted out will cause standard pins (publicly view-able pins) to be deleted or refused. Wireless Names or hardware IDs that have been opted out will cause custom pins (non-public, developer-based pins) to be moved to the next similar ambient signal that is not opted out. This is done via a system algorithm that understands neighboring ambient signals via API usage and ensures the hardware ID opted-out stays unused, while at the same time ensuring the app developer can count on the functionality needed for her application. The infrastructure will adjust custom pins as required to meet the privacy needs of the owners while maximizing the usefulness and availability for all wireless device software developers. Pins cannot be deleted by anyone other than the wireless name or Hardware ID owner or via system management processes. Pins can also never be edited once created.

###Data Security for The Developer
 
Custom pins use complex pin types which can be up to 256 characters (a hash for example) and this serves as the security token for the developer. No one can query your pins back without explicitly asking for your pin type. The longer and more complex your pin type, the more secure it is. You may also choose to share or make obvious pin types. There are no limits on the number of pin types you use or the variation of pin types you use. The content data of the pin should generally be codes or URLs pointing to data in your secure system, or it may be data that only your app will understand. This data can be up to 65k characters. The system stores only these short linkages - actual media content and any other type of content should be stored on your secure servers or any other service you choose to use. This means that the API stores and retrieves linkages between wireless identifiers and content that you store elsewhere. 
  
###Data Security for Wireless Name and Hardware ID Owners
 
Public pins and all account information is stored on highly secure redundant cloud services. The system is SSL throughout and all data is stored encrypted. The wireless name or hardware ID owner has the ability to add or delete all public pins associated to wireless names they own at any time.
 
###Use of Standard Pin Types

Standard pins are publicly view-able unless deleted or blocked by the wireless name owner. When an application requests pins associated with a wireless name or hardware ID it encounters, it can request all standard (public) pins, or in the interest of not being overwhelmed, it may request only a certain type, such as audio or a social media profile. Since a large number of wireless names and hardware IDs can be checked at once (say 500 wireless names detected in one location), using pin types will refine the search to what the app developer is interested in. Note that custom types are refined by their very nature of requiring the single, specific custom type - the pin type that the developer is interested in checking for on a group of wireless names or IDs detected by the wireless device running the application.
 

###Date Parameters
 
Careful use of the startDate and endDate parameters on the get function will ensure you get recent pins or older pins, or a correct count of pins for the day and time range you are interested in. These parameters allow you to ensure the data is not stale based on whatever is stale for your application. CreatedAt date and time can be used to indicate immediate between two devices via the simultaneous detection of the same unique WirelessName~HarewareID combination.






 
     
