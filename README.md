<h2 align="center">
   <a href="https://www.fox-ess.com">FoxESS</a> and<a href="https://www.home-assistant.io"> Home Assistant</a> integration via Modbus RS485
   </br></br>
   <img src="https://github.com/home-assistant/brands/raw/master/custom_integrations/foxess/logo.png" >
   </br>
</h2>


**A community maintained Home Assistant integration using local native polling of Modbus data using RS485 to enable near realtime data access, with no reliance on the FoxESS cloud portal**

![image](https://user-images.githubusercontent.com/6324545/166502285-eb0ca405-05a3-4722-a698-36e3e6b0f60d.png)


---

Connecting to your H3 inverter can be acheived by:  
   
* Connecting to the COM port using a [RS485 to USB](https://www.reichelt.de/raspberry-pi-usb-rs485-schnittstelle-ch340c-rpi-usb-rs485-p242783.html?&nbc=1) (Approved)
⚠️ Additional hardware requires basic electronics competencies to connect the two additional wires for the RS485 interface to the inverters com connector.⚠️

⚠️ Using the inverters LAN port connected to your router/switch (no additional hardware required) could not be approved for H3 inverters. Port 502 was not open. This solution might be fixed with future firmware. It is not possible with firmware version Master 1.25, Slave 1.02, Manage 1.29 ⚠️
 


---


## Supported Hardware
This fork adds support for the <br><img align="right" width=200 src="https://user-images.githubusercontent.com/13150440/200159634-6bfa1123-b9eb-4f78-b89a-3da9743b2b6f.PNG">
**Hybrid Series H3**<br>
Tested with<br>
✅ H3-8.0-E <br>
✅ H3-10.0-E <br>
<br>
Designed but not tested: <br>
 H3-5.0-E <br>
 H3-6.0-E <br>

 H3-12.0-E <br>
Please report if everything works well with these.

The [origin project](https://github.com/StealthChesnut/HA-FoxESS-Modbus) supports 1-phase Inverters
**Hybrid Series** <br> <img align="right" width=200 src="https://user-images.githubusercontent.com/6324545/166170598-7077d481-4d65-49b5-9816-1873c97dd853.png" >
✅ H1-3.0-E <br>
✅ H1-3.7-E <br>
✅ H1-4.6-E <br>
✅ H1-5.0-E <br>
✅ H1-6.0-E <br>
**AC Series** <br>
✅ AC-3.0-E <br>
✅ AC-3.7-E <br>
✅ AC-4.6-E <br>
✅ AC-5.0-E <br>
✅ AC-6.0-E <br>
**AIO Series** <br>
✅ AIO-H1-3.0 <br>
✅ AIO-H1-3.7 <br>
✅ AIO-H1-4.6 <br>
✅ AIO-H1-5.0 <br>
✅ AIO-H1-6.0 <br>

**For T Series - See [this alternative project](https://github.com/assembly12/Foxess-T-series-ESPHome-Home-Assistant) by [assembly12](https://github.com/assembly12)** <br>

---

<p>The aim of this project is to enable the full use of the Energy dashboard in Home Assistant and is a fully functional replacement of the FoxESS App for reporting needs.</p>

## HACS Specific Installation (not tested)
* Add this repository to your HACS custom integrations
* Install from HACS

## Manual Specific installation
* Create the directory structure /config/custom_components/HA-FoxESS-Modbus/ (use the "file editor" addon of HA)
* Copy the Required modbus file to /config/custom_components/HA-FoxESS-Modbus/modbusH3USB.yaml

## Then, Common Installation Steps

* Create a full backup of your HA instance including the configuration.yaml file
* Copy the Required modbus line (USB) and following contents of the [configuration.yaml](https://github.com/rsaemann/HA-FoxESS-H3-Modbus/blob/main/custom_components/HA-FoxESS-Modbus/configuration.yaml) file to your config file
* Check your config is valid, then Restart HA
* Map energy dashboard as per below example and enjoy configuring dashboards using near realtime data.


[Step by step walkthrough of the setup](https://youtu.be/uMPr0V6lTHg)
![image](https://user-images.githubusercontent.com/6324545/166504169-81fd77e8-df5b-40f0-9c1f-9735e59b2723.png)

## Engergy Dashboard Configuration

![image](https://user-images.githubusercontent.com/6324545/166470207-44236718-3f6c-4995-99fe-0a214eda49e6.png)
 

### Energy Dashboard Values

**Electricity Grid**
- eps-daily
- consumption-daily

**Solar Panels**

- pv1_daily
- pv2_daily

**Home Batteries**

- bat_charge_daily
- bat_discharge_daily

## Provided Entities

**Registers**
**The [H3 registers wiki](https://github.com/rsaemann/HA-FoxESS-H3-Modbus/wiki/H3-Modbus-Registers) has references for the 3-phase registers.**

**The [H1 registers wiki](https://github.com/StealthChesnut/HA-FoxESS-Modbus/wiki/Data-Register-Reference---H1-AC1) shows the 1-phase registers.**


<br>
<br>

---

Please read and understand before using this plugin:

> This plugin has been developed as a personal project, with no connection to the official brand of FoxESS, use of this plugin is intended for use by the community without fee but has no warrenty or liability should any damage, harm or undesired results happen as a result of using this plugin. We strongly recommend that only competently trained individuals attempt to wire the additional connections required for this plugin to function. There is a risk of personal or device damage/harm.
You have been warned!

---

