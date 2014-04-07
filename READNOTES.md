##Proximal API v2.0 - Aditional Notes

###Email to a Wireless Name

Emailing to a wireless name is possible using the format WirelessName@WirelessRegistry.com or HarwareID@WirelessRegistry.com. The email will enter the system and be forwarded immediately to the Wireless Name owner who can then respond directly to the original sender. Emails can also be sent to a Hardware ID in the same manner, for example AB-12-AB-12-AB-12@wirelessregistry.com or AB12AB12AB12@wirelessregistry.com and flow through to the registered owner. Innovative use cases can be built where a router of any kind can contact a device directly via the wireless ID string without a direct connection to it.
  
###Wireless Name Public URL for public Pins

All wireless strings may have public content associated with them and this content can be seen at www.WirelessRegistry.com/WirelessName or www.WirelessRegistry.com/HardwareID. This page shows all public content, such as standard pins, that is associateed to the wireless string and allowed by the registered owner. www.WirelessRegistry.com/WirelessName~HaredwareID will take the user directly to just the content assocated to that particular wirless name and hardwareID combination.
 
###Wireless Technology and Spectrum

Note that the wireless signals in question are independent of the technology or spectrum then are transmitted on. A wireless name can be transmitted on Wi-Fi, Bluetooth, BLE, LTE-Direct or any other technology on any spectrum. Distance and signal strength are also not included as these are managed on device by your software. You may choose to check a wireless signal for pins or to pin to a wireless signal based on the type of signal or based on a signal strength. This is all done on device under your control. You may pin different custom pin types for different types of signals - for Bluetooth, or Wi-Fi, or LTE-Direct for example. You may inlude the signal strength or any other data you wish in the data payload of the pin. This is all up to the developer and the combinations allow for creative implementations.
       
###Tilde

Throughout the documentation and in recommended use-cases you will note the use of the tilde "~". This character will be used as an indicator of a wireless name (~MyWirelessName) as well as a separator between wireless names and a related hardware ID (MyWirelessName~AB:12:AB:12:AB:12).
 
###Pin Ownership, Overall Data Ownership

The Wireless Registry considers all data in the system to be owned and controlled by the registered wirless string owners. This means registrants of a wireless name control all Public pins at all times. HardwareID registrants similarly control all pins, both Standard pins and Custom pins. Developers can freely add pins to any wireless signal at no cost and also query the system without restriction or cost - and the Registry and API infrasture of The Wireless Registry will automatically ensure the pins respect the privacy settings and control requests of all Wireless Name and Hardware ID owners. The infrastructure will adjust pins as required to meet the requests and privacy needs of the owners while maximizing the usefullness and availability for all wireless device software developers. Pins cannot be deleted by anyone other than the wireless name or Hardware ID owner, and pins can never be modified once created. 

###Data Security for The Developer
 
Custom pins use complex pin types which can be up to 256 character (a hash for example) and this serves as the security token for the developer. No one can query your pins back without explicitily asking for your pin type. The longer and more complex your pin type, the more secure it is. You may also choose to share or make obvious pin types. The data in the pin can be strictly codes pointing to data in your secure system or data that only your app will understand. This data can be up to 65k characters. The system stores only these short linkages and media content and any other type of content should be stored on your secure servers or any other service you choose to use. The API stores and retrieves linkages between wireless identifiers and content you store elseware.
 
###Data Security for Wireless Name and Hardware ID Owners
 
Public pins and all account information is stored on highly secure redundant cloud services. The system is SSL throughout and all data is stored encrypted. The wireless name owner has the ability to add or delete all public pins associated to wireless names they own at any time.
 



 
     
