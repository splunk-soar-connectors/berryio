[comment]: # "Auto-generated SOAR connector documentation"
# BerryIO

Publisher: Splunk Community  
Connector Version: 2\.0\.3  
Product Vendor: Daniel Bull  
Product Name: BerryIO  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.10\.0\.40961  

This app supports actions for APIs on the BerryIO project for the Raspberry Pi, such as GPIO status, get and set

[comment]: # ""
[comment]: # "File: readme.md"
[comment]: # ""
[comment]: # "Copyright (c) 2016-2021 Splunk Inc."
[comment]: # ""
[comment]: # "Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
[comment]: # ""
See the [BerryIO](https://github.com/NeonHorizon/berryio) project for more information.

For BerryIO API features that are not supported as part of this app, such as taking an image with
the camera, you can make use of the Phantom HTTP app to perform a generic http post. Just configure
an asset to use the HTTP app with your BerryIO basic auth.

To make this app python3 compatible check
[this](https://docs.splunk.com/Documentation/SOARonprem/5.0.1/DevelopApps/Python3) link.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a BerryIO asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  optional  | string | Base URL
**username** |  required  | string | Username
**password** |  required  | password | Password
**verify\_server\_cert** |  optional  | boolean | Verify server certificate

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity\. This action logs into the device to check the connection and credentials  
[set mode](#action-set-mode) - Set GPIO Mode  
[set value](#action-set-value) - Set GPIO Value  
[get status](#action-get-status) - Get GPIO status  

## action: 'test connectivity'
Validate the asset configuration for connectivity\. This action logs into the device to check the connection and credentials

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'set mode'
Set GPIO Mode

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**mode** |  required  | GPIO Mode \(in/out/not\_exported\) | string |  `gpio mode` 
**pin** |  required  | GPIO Pin | numeric |  `gpio pin` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.raw | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.parameter\.pin | string |  `gpio pin` 
action\_result\.parameter\.mode | string |  `gpio mode` 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'set value'
Set GPIO Value

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**value** |  required  | GPIO Value \(0/1\) | numeric |  `gpio value` 
**pin** |  required  | GPIO Pin | numeric |  `gpio pin` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.raw | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.parameter\.pin | string |  `gpio pin` 
action\_result\.parameter\.value | string |  `gpio value` 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get status'
Get GPIO status

Type: **generic**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.raw | string | 
action\_result\.data\.\*\.gpio\.\*\.pin | string |  `gpio pin` 
action\_result\.data\.\*\.gpio\.\*\.mode | string |  `gpio mode` 
action\_result\.data\.\*\.gpio\.\*\.value | string |  `gpio value` 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 