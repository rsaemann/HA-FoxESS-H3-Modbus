**. ➡ This Fork is not updated any more as I recommend using the HA Integration by @Nathan Marlor [https://github.com/nathanmarlor/foxess_modbus](https://github.com/nathanmarlor/foxess_modbus) for H3 inverters. 👍 .**
<br>

<h2 align="center">
   <a href="https://www.fox-ess.com">FoxESS</a> and<a href="https://www.home-assistant.io"> Home Assistant</a> integration via Modbus RS485
   </br></br>
   <img src="https://github.com/home-assistant/brands/raw/master/custom_integrations/foxess/logo.png" >
   </br>
</h2>


**A community maintained Home Assistant integration using local native polling of Modbus data using RS485 to enable near realtime data access, with no reliance on the FoxESS cloud portal**

![image](https://user-images.githubusercontent.com/6324545/166502285-eb0ca405-05a3-4722-a698-36e3e6b0f60d.png)


---

Connecting your H3 inverter can be acheived by:  
   
* Connecting to the (RasPi's) COM port using a [RS485 to USB](https://www.reichelt.de/raspberry-pi-usb-rs485-schnittstelle-ch340c-rpi-usb-rs485-p242783.html?&nbc=1) (Approved)
* Connecting to the home WiFi using a RS485 to WiFi dongle like the 'Elfin EW11A RS485 to WIFI converter'. [HowTo in the Wiki.](https://github.com/rsaemann/HA-FoxESS-H3-Modbus/wiki/RS485-via-Wifi) (Connects the RS485 pins on your inverter. This does not use the inverter's build-in WiFi or Ethernet connection.)

* ⚠️ Using the inverter's Ethernet LAN port or dongle to connect to your router/switch via Ethernet does **not** work for H3 inverters, yet. Port 502 is not open. This solution might be fixed with future firmware. It is not possible with firmware version Master 1.25-1.57, Slave 1.02, Manager 1.29 ⚠️
 


---


## Supported Hardware
This fork adds support for the <br><img align="right" width=180 src="https://user-images.githubusercontent.com/13150440/200159634-6bfa1123-b9eb-4f78-b89a-3da9743b2b6f.PNG">
**Hybrid Series H3**<br>
Tested with<br>
✅ H3-5.0-E <br>
✅ H3-6.0-E <br>
✅ H3-8.0-E <br>
✅ H3-10.0-E <br>
✅ H3-12.0-E <br>
<br>

The [origin project](https://github.com/StealthChesnut/HA-FoxESS-Modbus) supports 1-phase Inverters
**Hybrid Series** <br> 
✅ H1-3.0-E <br>
✅ H1-3.7-E <br>
✅ H1-4.6-E <br>
✅ H1-5.0-E <br>
✅ H1-6.0-E <br>
**AC Series** <br><img align="right" width=180 src="https://user-images.githubusercontent.com/6324545/166170598-7077d481-4d65-49b5-9816-1873c97dd853.png" >
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

## ⚠️ Installation via HACS does not work for this fork due to naming convention

## Manual Specific installation
* Create the directory structure /config/custom_components/HA-FoxESS-Modbus/ (use the "file editor" addon of HA)
* Copy the required modbus file to /config/custom_components/HA-FoxESS-Modbus/
  * if you go with serial cable to USB connection use /config/custom_components/HA-FoxESS-Modbus/modbusH3USB.yaml
  * if you go with wifi to RS485 dongle use /config/custom_components/HA-FoxESS-Modbus/modbusLAN-H3.yaml

## Then, Common Installation Steps

* Create a full backup of your HA instance including the configuration.yaml file
* Copy the required modbus line (USB or Wifi) and following contents of the [configuration.yaml](https://github.com/rsaemann/HA-FoxESS-H3-Modbus/blob/main/custom_components/HA-FoxESS-Modbus/configuration.yaml) file to your config file
* Check your config is valid, then Restart HA
* Map energy dashboard as per below example and enjoy configuring dashboards using near realtime data.


[Step by step walkthrough of the setup (for the H1 inverter fork)](https://youtu.be/uMPr0V6lTHg)
![image](https://user-images.githubusercontent.com/6324545/166504169-81fd77e8-df5b-40f0-9c1f-9735e59b2723.png)

## Engergy Dashboard Configuration

![image](https://user-images.githubusercontent.com/6324545/166470207-44236718-3f6c-4995-99fe-0a214eda49e6.png)
 

### Energy Dashboard Values

**Grid Consumption**
- meter_consumption_energy_daily  (only when SmartMeter is connected to inverter)
- inv_load_energy_daily  (inverter's output. use for island system)

**Return to Grid**
- meter_feed_in_energy_daily (only when SmartMeter is connected to inverter)

**Solar Panels**

- pv1_daily
- pv2_daily

  As an alternative:
- pv_energy_daily (direct cumulative PV1+PV2 from inverter)

**Home Batteries**

- battery_charge_energy_daily
- battery_discharge_energy_daily

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
> This modbus integration is read-only. You cannot change the behaviour of your inverter or set any values.
---
## Troubleshooting

If you encounter modbus reading errors:
- Disable unneeded sensors by commenting all lines, or delete the entries. [It was found](https://github.com/StealthChesnut/HA-FoxESS-Modbus/issues/62) that ``battery_voltage`` and ``battery_current`` are two sensors that do not respond to status requests correctly.
  <details><summary>Comment out in the modbusH3USB.yaml file</summary>
   <p>
      
  ```
  #  - name: "Battery Voltage"
  #    unique_id: foxess_inv1_battery_voltage
  #    scan_interval: 30
  #    address: 31034
  #    state_class: measurement
  #    unit_of_measurement: "V"
  #    data_type: int16
  #    scale: 0.1
  #    precision: 1
  #    device_class: voltage
  #    input_type: holding
  #  - name: "Battery Current"
  #    unique_id: foxess_inv1_battery_current
  #    scan_interval: 30
  #    address: 31035
  #    state_class: measurement
  #    unit_of_measurement: "A"
  #    data_type: int16
  #    scale: 0.1
  #    precision: 1
  #    input_type: holding      
  #    device_class: current
  ```
      
   </p>
</details>

- Increase the ``scan_interval`` for sensors that are not needed. The HA modbus integration requests every sensor register with a single call. If you have a large number of sensors here, the calls might interfere with each other.
