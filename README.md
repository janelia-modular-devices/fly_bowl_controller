- [Repository Information](#org4b13de3)
  - [Description](#org82d2c91)
- [Images](#orgefc533a)
- [Usage Instructions](#org31177e9)
  - [Example Code](#org3ca9c4e)
    - [Arduino Serial Monitor](#orge8a6892)
    - [Python](#org8c8a48e)
    - [Matlab](#org00a3e70)
  - [Example Experiment Step Waveform](#org5212937)
    - [Step Duration](#org06584ea)
    - [Step Delay](#orgf61f7eb)
    - [Sequence Count](#orgfa07583)
    - [Sequence Off Duration](#org69b5d81)
    - [Pulse Count](#org7971cc7)
    - [Pulse On Duration](#org93c76fd)
    - [Pulse Period](#orgc7a5224)
    - [Power](#org59356ae)
- [Build Instructions](#org9ae033b)
- [Hardware](#org7936c62)
  - [backlight\_controller\_5x3](#org0aa09c7)
    - [Repository Information](#org1e404b1)
    - [Images](#orgb30a0f8)
    - [Schematic](#org30c02a4)
    - [Gerbers](#org97b59a6)
    - [Bill of Materials](#org9167bb9)
    - [Supplemental Documentation](#orgfadb06f)
  - [fly\_bowl\_wiring](#orge77fd92)
    - [Repository Information](#org37c28cd)
    - [Images](#org816b133)
    - [Schematic](#org60f2c4c)
    - [Gerbers](#org77ee25b)
    - [Bill of Materials](#orgb862eed)
    - [Supplemental Documentation](#org3b02220)
- [Firmware](#org74733a0)
  - [FlyBowlController](#org5587f95)
    - [Library Information](#org2cf10b9)
    - [API NAMES](#org2615ab7)
    - [API GENERAL](#org237b804)
    - [Ancestors](#orgb9ae9c8)
    - [Clients](#org6216257)
    - [Devices](#org0074993)
    - [More Detailed Modular Device Information](#org5a202a4)
    - [Installation Instructions](#org62d30a5)



<a id="org4b13de3"></a>

# Repository Information

-   **Name:** fly\_bowl\_controller
-   **Version:** 1.0
-   **License:** BSD, Open-Source Hardware
-   **URL:** <https://github.com/janelia-modular-devices/fly_bowl_controller>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com


<a id="org82d2c91"></a>

## Description

This device controls the IR and visible backlights in the fly bowl rig along with the backlight cooling fans and indicator lights.


<a id="orgefc533a"></a>

# Images

![img](./images/front_top.png)

![img](./images/top_bowls.png)

![img](./images/wired.png)


<a id="org31177e9"></a>

# Usage Instructions


<a id="org3ca9c4e"></a>

## Example Code


<a id="orge8a6892"></a>

### Arduino Serial Monitor

```sh
?
# {
#   "id": "?",
#   "result": {
#     "device_id": {
#       "name": "fly_bowl_controller",
#       "form_factor": "5x3",
#       "serial_number": 0
#     },
#     "api": {
#       "firmware": [
#         "FlyBowlController"
#       ],
#       "verbosity": "NAMES",
#       "functions": [
#         "setIrBacklightsOnAtPower",
#         "setVisibleBacklightsOnAtPower",
#         "addVisibleBacklightsPwm",
#         "addExperimentStep",
#         "getExperimentSteps",
#         "getExperimentStatus"
#       ],
#       "parameters": [
#         "pulse_delay",
#         "pulse_period",
#         "pulse_on_duration",
#         "pulse_count",
#         "sequence_off_duration",
#         "sequence_count",
#         "step_delay",
#         "step_duration"
#       ],
#       "properties": [
#         "flyBowlsEnabled"
#       ],
#       "callbacks": [
#         "setIrBacklightsOn",
#         "setIrBacklightsOff",
#         "setVisibleBacklightsOn",
#         "setVisibleBacklightsOff",
#         "removeAllExperimentSteps",
#         "runExperiment",
#         "stopExperiment"
#       ]
#     }
#   }
# }
setPropertiesToDefaults [ALL]
# {
#   "id": "setPropertiesToDefaults",
#   "result": null
# }
flyBowlsEnabled getValue
# {
#   "id": "flyBowlsEnabled",
#   "result": [
#     true,
#     true,
#     true,
#     true
#   ]
# }
flyBowlsEnabled setValue [true,false,true,false]
# {
#   "id": "flyBowlsEnabled",
#   "result": [
#     true,
#     false,
#     true,
#     false
#   ]
# }
setIrBacklightsOnAtPower 25
# {
#   "id": "setIrBacklightsOnAtPower",
#   "result": null
# }
removeAllExperimentSteps
# {
#   "id": "removeAllExperimentSteps",
#   "result": null
# }
addExperimentStep ?
# {
#   "id": "addExperimentStep",
#   "result": {
#     "name": "addExperimentStep",
#     "firmware": "FlyBowlController",
#     "parameters": [
#       "power",
#       "pulse_period",
#       "pulse_on_duration",
#       "pulse_count",
#       "sequence_off_duration",
#       "sequence_count",
#       "step_delay",
#       "step_duration"
#     ],
#     "result_info": {
#       "type": "long"
#     }
#   }
# }
addExperimentStep 25 100 50 5 750 4 1.0 6.0
# {
#   "id": "addExperimentStep",
#   "result": 0
# }
addExperimentStep 40 100 50 35 2500 4 0.0 20.0
# {
#   "id": "addExperimentStep",
#   "result": 1
# }
getExperimentSteps
# {
#   "id": "getExperimentSteps",
#   "result": [
#     {
#       "power": 25.000000,
#       "pulse_period": 100,
#       "pulse_on_duration": 50,
#       "pulse_count": 5,
#       "sequence_off_duration": 750,
#       "sequence_count": 4,
#       "step_delay": 1.000000,
#       "step_duration": 6.000000
#     },
#     {
#       "power": 40.000000,
#       "pulse_period": 100,
#       "pulse_on_duration": 50,
#       "pulse_count": 35,
#       "sequence_off_duration": 2500,
#       "sequence_count": 4,
#       "step_delay": 0.000000,
#       "step_duration": 20.000000
#     }
#   ]
# }
getExperimentStatus
# {
#   "id": "getExperimentStatus",
#   "result": {
#     "state": "EXPERIMENT_NOT_RUNNING",
#     "experiment_step_index": 0,
#     "experiment_step_count": 2,
#     "sequence_index": 0,
#     "sequence_count": 0
#   }
# }
runExperiment
# {
#   "id": "runExperiment",
#   "result": null
# }
getExperimentStatus
# {
#   "id": "getExperimentStatus",
#   "result": {
#     "state": "EXPERIMENT_RUNNING",
#     "experiment_step_index": 0,
#     "experiment_step_count": 2,
#     "sequence_index": 2,
#     "sequence_count": 4
#   }
# }
getExperimentStatus
# {
#   "id": "getExperimentStatus",
#   "result": {
#     "state": "EXPERIMENT_NOT_RUNNING",
#     "experiment_step_index": 0,
#     "experiment_step_count": 2,
#     "sequence_index": 0,
#     "sequence_count": 0
#   }
# }
setVisibleBacklightsOnAtPower 68
# {
#   "id": "setVisibleBacklightsOnAtPower",
#   "result": null
# }
setVisibleBacklightsOff
# {
#   "id": "setVisibleBacklightsOff",
#   "result": null
# }
addVisibleBacklightsPwm ?
# {
#   "id": "addVisibleBacklightsPwm",
#   "result": {
#     "name": "addVisibleBacklightsPwm",
#     "firmware": "FlyBowlController",
#     "parameters": [
#       "power",
#       "pulse_delay",
#       "pulse_period",
#       "pulse_on_duration",
#       "pulse_count"
#     ],
#     "result_info": {
#       "type": "long"
#     }
#   }
# }
addVisibleBacklightsPwm 100 5000 100 50 1000
# {
#   "id": "addVisibleBacklightsPwm",
#   "result": 0
# }
stopPwm 0
# {
#   "id": "stopPwm",
#   "result": null
# }
setIrBacklightsOff
# {
#   "id": "setIrBacklightsOff",
#   "result": null
# }
```


<a id="org8c8a48e"></a>

### Python

```python
from modular_client import ModularClient
dev = ModularClient() # Automatically finds device if one available
dev.get_device_id()
# {'name': 'fly_bowl_controller', 'form_factor': '5x3', 'serial_number': 0}
dev.set_properties_to_defaults(['ALL'])
dev.fly_bowls_enabled('getValue')
# [True, True, True, True]
dev.fly_bowls_enabled('setValue',[True,False,True,False])
# [True, False, True, False]
dev.set_ir_backlights_on_at_power(25) # 25 percent. Automatically turns fans on too
dev.remove_all_experiment_steps()
power = 25 # 25 percent
pulse_period = 100 # 100 ms
pulse_on_duration = 50 # 50 ms
pulse_count = 5
sequence_off_duration = 750 # 750 ms
sequence_count = 4
step_delay = 1.0 # 1.0 s
step_duration = 6.0 # 6.0 s
dev.add_experiment_step(power,
                        pulse_period,
                        pulse_on_duration,
                        pulse_count,
                        sequence_off_duration,
                        sequence_count,
                        step_delay,
                        step_duration)
# 0
power = 40 # 40 percent
pulse_period = 100 # 100 ms
pulse_on_duration = 50 # 50 ms
pulse_count = 35
sequence_off_duration = 2500 # 2500 ms
sequence_count = 4
step_delay = 0.0 # 0.0 s
step_duration = 20.0 # 20.0 s
dev.add_experiment_step(power,
                        pulse_period,
                        pulse_on_duration,
                        pulse_count,
                        sequence_off_duration,
                        sequence_count,
                        step_delay,
                        step_duration)
# 1
dev.get_experiment_steps()
# [{'power': 25.0,
#   'pulse_period': 100,
#   'pulse_on_duration': 50,
#   'pulse_count': 5,
#   'sequence_off_duration': 750,
#   'sequence_count': 4,
#   'step_delay': 1.0,
#   'step_duration': 6.0},
#  {'power': 40.0,
#   'pulse_period': 100,
#   'pulse_on_duration': 50,
#   'pulse_count': 35,
#   'sequence_off_duration': 2500,
#   'sequence_count': 4,
#   'step_delay': 0.0,
#   'step_duration': 20.0}]
dev.get_experiment_status()
# {'state': 'EXPERIMENT_NOT_RUNNING',
#  'experiment_step_index': 0,
#  'experiment_step_count': 2,
#  'sequence_index': 0,
#  'sequence_count': 0}
dev.run_experiment()
dev.get_experiment_status()
# {'state': 'EXPERIMENT_RUNNING',
#  'experiment_step_index': 0,
#  'experiment_step_count': 2,
#  'sequence_index': 3,
#  'sequence_count': 4}
#
# wait until experiment finishes or dev.stop_experiment()
dev.get_experiment_status()
# {'state': 'EXPERIMENT_NOT_RUNNING',
#  'experiment_step_index': 0,
#  'experiment_step_count': 2,
#  'sequence_index': 0,
#  'sequence_count': 0}
dev.set_visible_backlights_on_at_power(68) # 68 percent
dev.set_visible_backlights_off()
dev.add_visible_backlights_pwm('?')
# {'name': 'addVisibleBacklightsPwm',
#  'firmware': 'FlyBowlController',
#  'parameters': ['power',
#                 'pulse_delay',
#                 'pulse_period',
#                 'pulse_on_duration',
#                 'pulse_count'],
#  'result_info': {'type': 'long'}}
power = 100 # 100 percent
pulse_delay = 1000 # 1000 ms
pulse_period = 100 # 100 ms
pulse_on_duration = 50 # 50 ms
pulse_count = 1000
pwm_index = dev.add_visible_backlights_pwm(power,
                                           pulse_delay,
                                           pulse_period,
                                           pulse_on_duration,
                                           pulse_count)
dev.stop_pwm(pwm_index)
dev.set_ir_backlights_off() # Automatically turns fans off too
```


<a id="org00a3e70"></a>

### Matlab

```matlab
% Linux and Mac OS X
ls /dev/tty*
% example Linux serial port
serial_port = '/dev/ttyACM0'
% example Mac OS X serial port
serial_port = '/dev/tty.usbmodem262471'
% Windows
getAvailableComPorts()
% 'COM1'
% 'COM4'
% example Windows serial port
serial_port = 'COM4';
dev = ModularClient(serial_port); % creates a device object
dev.open();                       % opens a serial connection to the device
dev.getDeviceId()
%          name: 'fly_bowl_controller'
%   form_factor: '5x3'
% serial_number: 0
dev.setPropertiesToDefaults({'ALL'});
dev.flyBowlsEnabled('getValue')
% [1]    [1]    [1]    [1]
dev.flyBowlsEnabled('setValue',{true,false,true,false})
% [1]    [0]    [1]    [0]
dev.setIrBacklightsOnAtPower(25); % 25 percent. Automatically turns on fans too
dev.removeAllExperimentSteps();
power = 25; % 25 percent
pulse_period = 100; % 100 ms
pulse_on_duration = 50; % 50 ms
pulse_count = 5;
sequence_off_duration = 750; % 750 ms
sequence_count = 4;
step_delay = 1.0; % 1.0 s
step_duration = 6.0; % 6.0 s
dev.addExperimentStep(power, ...
                      pulse_period, ...
                      pulse_on_duration, ...
                      pulse_count, ...
                      sequence_off_duration, ...
                      sequence_count, ...
                      step_delay, ...
                      step_duration)
% 0
power = 40; % 40 percent
pulse_period = 100; % 100 ms
pulse_on_duration = 50; % 50 ms
pulse_count = 35;
sequence_off_duration = 2500; % 2500 ms
sequence_count = 4;
step_delay = 0.0; % 0.0 s
step_duration = 20.0; % 20.0 s
dev.addExperimentStep(power, ...
                      pulse_period, ...
                      pulse_on_duration, ...
                      pulse_count, ...
                      sequence_off_duration, ...
                      sequence_count, ...
                      step_delay, ...
                      step_duration)
% 1
experiment_steps = dev.getExperimentSteps();
experiment_steps{1}
%                 power: 25
%          pulse_period: 100
%     pulse_on_duration: 50
%           pulse_count: 5
% sequence_off_duration: 750
%        sequence_count: 4
%            step_delay: 1
%         step_duration: 6
experiment_steps{2}
%                 power: 40
%          pulse_period: 100
%     pulse_on_duration: 50
%           pulse_count: 35
% sequence_off_duration: 2500
%        sequence_count: 4
%            step_delay: 0
%         step_duration: 20
dev.getExperimentStatus()
%                 state: 'EXPERIMENT_NOT_RUNNING'
% experiment_step_index: 0
% experiment_step_count: 2
%        sequence_index: 0
%        sequence_count: 0
dev.runExperiment()
dev.getExperimentStatus()
%                 state: 'EXPERIMENT_RUNNING'
% experiment_step_index: 0
% experiment_step_count: 2
%        sequence_index: 2
%        sequence_count: 4
%
% wait until experiment finishes or dev.stopExperiment()
dev.getExperimentStatus()
%                 state: 'EXPERIMENT_NOT_RUNNING'
% experiment_step_index: 0
% experiment_step_count: 2
%        sequence_index: 0
%        sequence_count: 0
dev.setVisibleBacklightsOnAtPower(68); % 68 percent
dev.setVisibleBacklightsOff();
power = 100; % 100 percent
pulse_delay = 1000; % 1000 ms
pulse_period = 100; % 100 ms
pulse_on_duration = 50; % 50 ms
pulse_count = 1000;
pwm_index = dev.addVisibleBacklightsPwm(power, ...
                                        pulse_delay, ...
                                        pulse_period, ...
                                        pulse_on_duration, ...
                                        pulse_count);
dev.stopPwm(pwm_index);
dev.setIrBacklightsOff();
dev.close();
clear dev;
```


<a id="org5212937"></a>

## Example Experiment Step Waveform

Yellow waveform shows visible backlight.

Blue waveform shows visible backlight indicator LED.


<a id="org06584ea"></a>

### Step Duration

step\_duration = 6.0 s

![img](./images/waveform/step_duration.png)


<a id="orgf61f7eb"></a>

### Step Delay

step\_delay = 1.0 s

![img](./images/waveform/step_delay.png)


<a id="orgfa07583"></a>

### Sequence Count

sequence\_count = 4

![img](./images/waveform/sequence_count.png)


<a id="org69b5d81"></a>

### Sequence Off Duration

sequence\_off\_duration = 750 ms

![img](./images/waveform/sequence_off_duration.png)


<a id="org7971cc7"></a>

### Pulse Count

pulse\_count = 4

![img](./images/waveform/pulse_count.png)


<a id="org93c76fd"></a>

### Pulse On Duration

pulse\_on\_duration = 50 ms

![img](./images/waveform/pulse_on_duration.png)


<a id="orgc7a5224"></a>

### Pulse Period

pulse\_period = 100 ms

![img](./images/waveform/pulse_period.png)


<a id="org59356ae"></a>

### Power

Power = 25%

![img](./images/waveform/power.png)


<a id="org9ae033b"></a>

# Build Instructions


<a id="org7936c62"></a>

# Hardware


<a id="org0aa09c7"></a>

## backlight\_controller\_5x3


<a id="org1e404b1"></a>

### Repository Information

-   **Name:** backlight\_controller\_5x3
-   **Version:** 1.2
-   **License:** Open-Source Hardware
-   **URL:** <https://github.com/janelia-kicad/backlight_controller_5x3>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    This board controls up to four Smart Vision backlights with IR and visible channels plus additional high and low power channel outputs.


<a id="orgb30a0f8"></a>

### Images

![img](./images/backlight_controller_5x3/images/top.png)

![img](./images/backlight_controller_5x3/images/bottom.png)


<a id="org30c02a4"></a>

### Schematic

[./hardware/backlight\_controller\_5x3/schematic/backlight\_controller\_5x3.pdf](./hardware/backlight_controller_5x3/schematic/backlight_controller_5x3.pdf)

![img](./images/backlight_controller_5x3/schematic/images/schematic00.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic01.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic02.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic03.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic04.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic05.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic06.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic07.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic08.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic09.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic10.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic11.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic12.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic13.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic14.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic15.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic16.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic17.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic18.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic19.png)

![img](./images/backlight_controller_5x3/schematic/images/schematic20.png)


<a id="org97b59a6"></a>

### Gerbers

Send gerbers zip file to your favorite PCB manufacturer for fabrication.

[./hardware/backlight\_controller\_5x3/gerbers/backlight\_controller\_5x3\_v1.2.zip](./hardware/backlight_controller_5x3/gerbers/backlight_controller_5x3_v1.2.zip)

![img](./images/backlight_controller_5x3/gerbers/images/gerbers00.png)

![img](./images/backlight_controller_5x3/gerbers/images/gerbers01.png)


<a id="org9167bb9"></a>

### Bill of Materials

1.  PCB Parts

    | Item | Reference(s)                                            | Quantity | PartNumber         | Vendor  | Description                                                               |
    |---- |------------------------------------------------------- |-------- |------------------ |------- |------------------------------------------------------------------------- |
    | 1    | C1 C2 C3 C4 C5 C6                                       | 6        | 399-13229-1-ND     | digikey | CAP CER 0.1UF 50V 10% X7R 1210                                            |
    | 2    | D1                                                      | 1        | 568-11697-1-ND     | digikey | DIODE SCHOTTKY 45V 10A CFP15                                              |
    | 3    | HPS1 HPS2 HPS3 HPS4                                     | 4        | BTS3256DAUMA1CT-ND | digikey | IC SWITCH SMART LOWSIDE TO252-5                                           |
    | 4    | J1                                                      | 1        | 1195-4005-1-ND     | digikey | CONN D-SUB RCPT 9POS SMD SOLDER                                           |
    | 5    | J10 J3 J4 J5 J6 J7 J8 J9                                | 8        | 277-10282-1-ND     | digikey | CONN FMALE INSERT 5POS SOLDER                                             |
    | 6    | J2                                                      | 1        | 1195-4006-1-ND     | digikey | CONN D-SUB PLUG 9POS SMD SOLDER                                           |
    | 7    | L1                                                      | 1        | 350-1723-ND        | digikey | LED 2MM 24V VERTICAL RED PC MNT                                           |
    | 8    | L10 L11 L12 L13 L14 L15 L16 L17 L2 L3 L4 L5 L6 L7 L8 L9 | 16       | 350-1726-ND        | digikey | LED 2MM 5V VERTICAL GREEN PC MNT                                          |
    | 9    | MDB1                                                    | 2        | S1011E-25-ND       | digikey | 25 Positions Header Breakaway Connector 0.1in                             |
    | 10   | P1                                                      | 1        | WM1353-ND          | digikey | CONN HEADER 6POS 4.2MM R/A TIN                                            |
    | 11   | R1 R2 R3 R4                                             | 4        | P5.90KAACT-ND      | digikey | RES SMD 5.9k OHM 1% 1/2W 1210                                             |
    | 12   | R5 R6 R7 R8                                             | 4        | P75.0CCT-ND        | digikey | RES SMD 75 OHM 1% 1/8W 0805                                               |
    | 13   | U1 U2                                                   | 2        | 296-14668-1-ND     | digikey | Buffer Non-Inverting 1 Element 8 Bit per Element Push-Pull Output 20-SOIC |
    | 14   | U10 U3 U4 U5 U6 U7 U8 U9                                | 8        | NUD3124LT1GOSCT-ND | digikey | IC INDCT LOAD DRVR AUTO SOT23                                             |

2.  Supplemental Parts

    | Item | Quantity | PartNumber   | Vendor  | Description                    |
    |---- |-------- |------------ |------- |------------------------------ |
    | 1    | 1        | 1866-2122-ND | digikey | AC/DC DESKTOP ADAPTER 24V 280W |
    | 2    | 1        | 1866-5006-ND | digikey | CORD IEC 320-C13 6FT BLACK     |
    | 3    | 8        | 277-10308-ND | digikey | CONN INSERT SHELL PRESS FIT    |

3.  Vendor Parts Lists

    [./hardware/backlight\_controller\_5x3/bom/digikey\_parts.csv](./hardware/backlight_controller_5x3/bom/digikey_parts.csv)

    [./hardware/backlight\_controller\_5x3/bom/supplemental\_digikey\_parts.csv](./hardware/backlight_controller_5x3/bom/supplemental_digikey_parts.csv)


<a id="orgfadb06f"></a>

### Supplemental Documentation

1.  Assembly Instructions

    -   Solder surface mount and through hole components onto the pcb.


<a id="orge77fd92"></a>

## fly\_bowl\_wiring


<a id="org37c28cd"></a>

### Repository Information

-   **Name:** fly\_bowl\_wiring
-   **Version:** 1.0
-   **License:** Open-Source Hardware
-   **URL:** <https://github.com/janelia-kicad/fly_bowl_wiring>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    Wiring schematics and documentation for the multiple fly bowl rig.


<a id="org816b133"></a>

### Images

![img](./images/fly_bowl_wiring/images/top.png)


<a id="org60f2c4c"></a>

### Schematic

[./hardware/fly\_bowl\_wiring/schematic/fly\_bowl\_wiring.pdf](./hardware/fly_bowl_wiring/schematic/fly_bowl_wiring.pdf)

![img](./images/fly_bowl_wiring/schematic/images/schematic00.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic01.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic02.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic03.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic04.png)


<a id="org77ee25b"></a>

### Gerbers


<a id="orgb862eed"></a>

### Bill of Materials

1.  PCB Parts

    | Item | Reference(s)                                                | Quantity | PartNumber     | Vendor            | Description                         |
    |---- |----------------------------------------------------------- |-------- |-------------- |----------------- |----------------------------------- |
    | 1    | BL1 BL2 BL3 BL4                                             | 4        | MOBL\_150x150  | smartvisionlights | Maximum Operating Backlight 150x150 |
    | 2    | CABLE1 CABLE2                                               | 2        | 1195-7211-ND   | digikey           | CABLE ASSY DB09 SHLD BEIGE 2M       |
    | 3    | CABLE10 CABLE11 CABLE13 CABLE14 CABLE4 CABLE5 CABLE7 CABLE8 | 8        | 277-8345-ND    | digikey           | CBL FMALE RA TO MALE 5POS 1.5M      |
    | 4    | CABLE12 CABLE3 CABLE6 CABLE9                                | 4        | GC14333-ND     | digikey           | USB3.0-A-USB3.0-MICRO-B 3M GOLD     |
    | 5    | CAMERA1 CAMERA2 CAMERA3 CAMERA4                             | 4        | FL3-U3-13Y3M-C | flir              | 1280x1024 150 FPS Mono              |
    | 6    | F1 F2 F3 F4 F5 F6 F7 F8                                     | 8        | 381-2367-ND    | digikey           | FAN AXIAL 40X10MM 24VDC WIRE        |
    | 7    | J1                                                          | 1        | 277-2667-ND    | digikey           | CONN DSUB PLUG 9POS STR TERM BLK    |
    | 8    | J2                                                          | 1        | 277-2668-ND    | digikey           | CONN DSUB RCPT 9POS STR TERM BLK    |
    | 9    | L1 L2 L3 L4                                                 | 4        | 475-2864-2-ND  | digikey           | EMITTER IR 860NM 100MA SMD          |

2.  Supplemental Parts

    | Item | Quantity | PartNumber  | Vendor  | Description                  |
    |---- |-------- |----------- |------- |---------------------------- |
    | 1    | 2        | 277-2684-ND | digikey | 9POS DSUB BACKSHELL          |
    | 2    | 2        | 277-2767-ND | digikey | DSUB CAP NUT W/SEAL          |
    | 3    | 2        | 277-2722-ND | digikey | DSUB CAP NUT W/SEAL          |
    | 4    | 2        | A33692-ND   | digikey | CONN D-SUB FEMALE SCREW LOCK |

3.  Vendor Parts Lists

    [./hardware/fly\_bowl\_wiring/bom/digikey\_parts.csv](./hardware/fly_bowl_wiring/bom/digikey_parts.csv)

    [./hardware/fly\_bowl\_wiring/bom/flir\_parts.csv](./hardware/fly_bowl_wiring/bom/flir_parts.csv)

    [./hardware/fly\_bowl\_wiring/bom/smartvisionlights\_parts.csv](./hardware/fly_bowl_wiring/bom/smartvisionlights_parts.csv)

    [./hardware/fly\_bowl\_wiring/bom/supplemental\_digikey\_parts.csv](./hardware/fly_bowl_wiring/bom/supplemental_digikey_parts.csv)


<a id="org3b02220"></a>

### Supplemental Documentation

1.  Assembly Instructions

    1.  Fly Bowl Numbering

        | Enclosure | Left | Right |
        |--------- |---- |----- |
        | Back      | 0    | 1     |
        | Front     | 2    | 3     |

    2.  Pinout

        | Fly Bowl | Description       | DB9 | Channel | Pin |
        |-------- |----------------- |--- |------- |--- |
        | 0        | IR BACKLIGHT      |     | 8       | 20  |
        | 0        | VISIBLE BACKLIGHT |     | 9       | 21  |
        | 0        | FAN               | 2   | 0       | 2   |
        | 0        | LED               | 2   | 4       | 30  |
        | 1        | IR BACKLIGHT      |     | 10      | 22  |
        | 1        | VISIBLE BACKLIGHT |     | 11      | 23  |
        | 1        | FAN               | 4   | 1       | 5   |
        | 1        | LED               | 4   | 5       | 14  |
        | 2        | IR BACKLIGHT      |     | 12      | 35  |
        | 2        | VISIBLE BACKLIGHT |     | 13      | 36  |
        | 2        | FAN               | 6   | 2       | 6   |
        | 2        | LED               | 6   | 6       | 18  |
        | 3        | IR BACKLIGHT      |     | 14      | 37  |
        | 3        | VISIBLE BACKLIGHT |     | 15      | 38  |
        | 3        | FAN               | 8   | 3       | 29  |
        | 3        | LED               | 8   | 7       | 19  |


<a id="org74733a0"></a>

# Firmware


<a id="org5587f95"></a>

## FlyBowlController


<a id="org2cf10b9"></a>

### Library Information

-   **Name:** FlyBowlController
-   **Version:** 2.0.1
-   **License:** BSD
-   **URL:** <https://github.com/janelia-arduino/FlyBowlController>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    Modular device fly bowl controller library.


<a id="org2615ab7"></a>

### API NAMES

```js
{
  "id": "getApi",
  "result": {
    "firmware": [
      "FlyBowlController"
    ],
    "verbosity": "NAMES",
    "functions": [
      "setIrBacklightsOnAtPower",
      "setVisibleBacklightsOnAtPower",
      "addVisibleBacklightsPwm",
      "addExperimentStep",
      "getExperimentSteps",
      "getExperimentStatus"
    ],
    "parameters": [
      "pulse_delay",
      "pulse_period",
      "pulse_on_duration",
      "pulse_count",
      "sequence_off_duration",
      "sequence_count",
      "step_delay",
      "step_duration"
    ],
    "properties": [
      "flyBowlsEnabled"
    ],
    "callbacks": [
      "setIrBacklightsOn",
      "setIrBacklightsOff",
      "toggleIrBacklights",
      "setVisibleBacklightsOn",
      "setVisibleBacklightsOff",
      "toggleVisibleBacklights",
      "removeAllExperimentSteps",
      "runExperiment",
      "stopExperiment"
    ]
  }
}
```


<a id="org237b804"></a>

### API GENERAL

<./firmware/FlyBowlController/api/>


<a id="orgb9ae9c8"></a>

### Ancestors

<https://github.com/janelia-arduino/ModularServer>

<https://github.com/janelia-arduino/ModularDeviceBase>

<https://github.com/janelia-arduino/DigitalController>

<https://github.com/janelia-arduino/BacklightController>


<a id="org6216257"></a>

### Clients


<a id="org0074993"></a>

### Devices

<https://github.com/janelia-modular-devices/modular_device_base>

<https://github.com/janelia-modular-devices/backlight_controller>

<https://github.com/janelia-modular-devices/fly_bowl_controller>


<a id="org5a202a4"></a>

### More Detailed Modular Device Information

<https://github.com/janelia-modular-devices/modular-devices>


<a id="org62d30a5"></a>

### Installation Instructions

<https://github.com/janelia-arduino/arduino-libraries>
