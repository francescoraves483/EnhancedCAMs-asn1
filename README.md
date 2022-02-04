# ASN.1 module for Enhanced Cooperative Awareness Messages
This repository contains the ASN.1 module for the enhanced version of Cooperative Awareness Messages (CAMs).
The enhanced version is a proposed addition to the ETSI EN 302 637-2 v1.4.1 (2019-04) standard, which defines the format for CAM messages (version 2), together with the rules for the transmission and reception of the messages themselves (i.e., the so-called Cooperative Awareness Basic Service).
The Enhanced CAMs are equal to standard CAMs, but for the addition of an extra optional container.

This container has been thought to store information about node and channel load, together with a few additional network parameters (such as IP addresses in case an IP stack is available in the sending and/or receiving ITS Station). This information is currently not found in any other ETSI message, to the best of our knowledge, even though it can be important to enable novel Vehicular Networking approaches, such as Vehicle Edge Computing or Vehicular Micro Clouds.

We propose thus a new container, called Channel and Node Status Container, which stores:
- CPU Load percentage (of the device sending the Enhanced CAMs)
- GPU Load percentage (of the device sending the Enhanced CAMs)
- Free RAM in MB (of the device sending the Enhanced CAMs)
- _(not yet implemented in the ASN.1 module)_ Free disk in MB (of the device sending the Enhanced CAMs)
- Extra device CPU Load percentage (of an optional extra computation device connected to the one sending the Enhanced CAMs)
- Extra device GPU Load percentage (of an optional extra computation device connected to the one sending the Enhanced CAMs)
- Extra device free RAM in MB (of an optional extra computation device connected to the one sending the Enhanced CAMs)
- _(not yet implemented in the ASN.1 module)_ Extra device free disk in MB (of an optional extra computation device connected to the one sending the Enhanced CAMs)
- Extra link RSSI (in case an extra radio interface, other than the main DSRC/C-V2X one, is available in a vehicle, its information can optionally be stored here)
- Extra link MAC address (in case an extra radio interface, other than the main DSRC/C-V2X one, is available in a vehicle, its information can optionally be stored here)
- Main link RSSI (RSSI of the DSRC V2V/V2I main channel)
- _(not yet implemented in the ASN.1 module)_ Main link data rate (data rate of the DSRC V2V/V2I main channel)
- Local IP address (if the vehicle is reachable in a private IPv4 network, its main IP address can be stored here)
- Public IP address (if the vehicle is offering some service, and it should be reachable, via IPv4, from the outside world or from the RSU, the IPv4 address from which it can be reached can be stored here)
- _(not yet implemented in the ASN.1 module)_ Up to 10 service IP addresses (optional field to store up to 10 extra IP addresses, depending on the user needs)

This repository contains the latest version of the ASN.1 module for the Enhanced CAMs. It has been designed to make it easy for an application to support both standard CAMs (without the possibility of adding the extra container) and enhanced CAMs. Standard CAMs can be generated starting from the "CAM" sequence, while Enhanced CAMs can be generated starting from the "CAMEnhanced" sequence. The additional container is optional even in enhanced CAMs.

The required [ITS-Container module](https://forge.etsi.org/rep/ITS/asn1/cdd_ts102894_2), from ETSI, is also included here.

If you want to use this module in a C/C++ program, you can generate the encoding/decoding C functions with tools like [asn1c](https://github.com/vlm/asn1c).

The original ASN.1 module for standard CAMs by ETSI can be found [here](https://forge.etsi.org/rep/ITS/asn1/cam_en302637_2/-/tree/master).

This module is currently being used in the [OCABS](https://github.com/francescoraves483/OCABS-project) and [AIM](https://github.com/francescoraves483/AIM-AutomotiveIntegratedMap) projects.

# License
The content of this repository and the files contained are released under the BSD-3-Clause license.

Please see the included LICENSE file.
