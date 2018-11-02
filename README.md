- [Repository Information](#orge0b85a8)
  - [Description](#orgfcedba9)
- [Images](#org67649b9)
- [Usage Instructions](#orgb080e15)
  - [Arduino Serial Monitor](#orgcb591e9)
  - [Python](#org00b1a56)
  - [Matlab](#orgbe41dce)
- [Build Instructions](#org51dca8f)
- [Hardware](#org81ab832)
  - [backlight\_controller\_5x3](#orge0a6299)
    - [Repository Information](#orga9deef9)
    - [Images](#org5d13867)
    - [Schematic](#org9ae0a59)
    - [Gerbers](#org2b07751)
    - [Bill of Materials](#orge833863)
    - [Supplemental Documentation](#orgb88f7c2)
  - [fly\_bowl\_wiring](#orgde4b725)
    - [Repository Information](#org0baba33)
    - [Images](#org61ef9ae)
    - [Schematic](#org6a3b711)
    - [Gerbers](#org2e8f92c)
    - [Bill of Materials](#org378a925)
    - [Supplemental Documentation](#org6a994d0)
- [Firmware](#orgf8aa930)
  - [FlyBowlController](#org07c5628)
    - [Library Information](#orgeeb161b)
    - [API NAMES](#org03e97ab)
    - [API GENERAL](#org51a8f4f)
    - [Ancestors](#org869aa89)
    - [Clients](#org0ac8120)
    - [Devices](#orge2642b2)
    - [More Detailed Modular Device Information](#orgf8bb024)
    - [Installation Instructions](#org6cb8631)



<a id="orge0b85a8"></a>

# Repository Information

-   **Name:** fly\_bowl\_controller
-   **Version:** 1.0
-   **License:** BSD, Open-Source Hardware
-   **URL:** <https://github.com/janelia-modular-devices/fly_bowl_controller>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com


<a id="orgfcedba9"></a>

## Description

This device controls the IR and visible backlights in the fly bowl rig along with the backlight cooling fans and indicator lights.


<a id="org67649b9"></a>

# Images

![img](./images/front_top.png)


<a id="orgb080e15"></a>

# Usage Instructions


<a id="orgcb591e9"></a>

## Arduino Serial Monitor

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
setIrBacklightsOnAtPower 90
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
addExperimentStep 90 100 50 25 2500 4 4.0 30.0
# {
#   "id": "addExperimentStep",
#   "result": 0
# }
addExperimentStep 75 100 50 35 2500 4 0.0 20.0
# {
#   "id": "addExperimentStep",
#   "result": 1
# }
getExperimentSteps
# {
#   "id": "getExperimentSteps",
#   "result": [
#     {
#       "power": 90,
#       "pulse_period": 100,
#       "pulse_on_duration": 50,
#       "pulse_count": 25,
#       "sequence_off_duration": 2500,
#       "sequence_count": 4,
#       "step_delay": 4.000000,
#       "step_duration": 30.000000
#     },
#     {
#       "power": 75,
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


<a id="org00b1a56"></a>

## Python

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
dev.set_ir_backlights_on_at_power(90) # 90 percent. Automatically turns fans on too
dev.remove_all_experiment_steps()
power = 90 # 90 percent
pulse_period = 100 # 100 ms
pulse_on_duration = 50 # 50 ms
pulse_count = 25
sequence_off_duration = 2500 # 2500 ms
sequence_count = 4
step_delay = 4.0 # 4.0 s
step_duration = 30.0 # 30.0 s
dev.add_experiment_step(power,
                        pulse_period,
                        pulse_on_duration,
                        pulse_count,
                        sequence_off_duration,
                        sequence_count,
                        step_delay,
                        step_duration)
# 0
power = 75 # 75 percent
pulse_count = 35
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
# [{'power': 90,
#   'pulse_period': 100,
#   'pulse_on_duration': 50,
#   'pulse_count': 25,
#   'sequence_off_duration': 2500,
#   'sequence_count': 4,
#   'step_delay': 4.0,
#   'step_duration': 30.0},
#  {'power': 75,
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


<a id="orgbe41dce"></a>

## Matlab

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
dev.setIrBacklightsOnAtPower(90); % 90 percent. Automatically turns on fans too
dev.removeAllExperimentSteps();
power = 90; % 90 percent
pulse_period = 100; % 100 ms
pulse_on_duration = 50; % 50 ms
pulse_count = 25;
sequence_off_duration = 2500; % 2500 ms
sequence_count = 4;
step_delay = 4.0; % 4.0 s
step_duration = 30.0; % 30.0 s
dev.addExperimentStep(power, ...
                      pulse_period, ...
                      pulse_on_duration, ...
                      pulse_count, ...
                      sequence_off_duration, ...
                      sequence_count, ...
                      step_delay, ...
                      step_duration)
% 0
power = 75; % 75 percent
pulse_count = 35;
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
%                 power: 90
%          pulse_period: 100
%     pulse_on_duration: 50
%           pulse_count: 25
% sequence_off_duration: 2500
%        sequence_count: 4
%            step_delay: 4
%         step_duration: 30
experiment_steps{2}
%                 power: 70
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


<a id="org51dca8f"></a>

# Build Instructions


<a id="org81ab832"></a>

# Hardware


<a id="orge0a6299"></a>

## backlight\_controller\_5x3


<a id="orga9deef9"></a>

### Repository Information

-   **Name:** backlight\_controller\_5x3
-   **Version:** 1.2
-   **License:** Open-Source Hardware
-   **URL:** <https://github.com/janelia-kicad/backlight_controller_5x3>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    This board controls up to four Smart Vision backlights with IR and visible channels plus additional high and low power channel outputs.


<a id="org5d13867"></a>

### Images


<a id="org9ae0a59"></a>

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


<a id="org2b07751"></a>

### Gerbers

Send gerbers zip file to your favorite PCB manufacturer for fabrication.

[./hardware/backlight\_controller\_5x3/gerbers/backlight\_controller\_5x3\_v1.2.zip](./hardware/backlight_controller_5x3/gerbers/backlight_controller_5x3_v1.2.zip)

![img](./images/backlight_controller_5x3/gerbers/images/gerbers00.png)

![img](./images/backlight_controller_5x3/gerbers/images/gerbers01.png)


<a id="orge833863"></a>

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


<a id="orgb88f7c2"></a>

### Supplemental Documentation

1.  Assembly Instructions

    -   Solder surface mount and through hole components onto the pcb.


<a id="orgde4b725"></a>

## fly\_bowl\_wiring


<a id="org0baba33"></a>

### Repository Information

-   **Name:** fly\_bowl\_wiring
-   **Version:** 1.0
-   **License:** Open-Source Hardware
-   **URL:** <https://github.com/janelia-kicad/fly_bowl_wiring>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description


<a id="org61ef9ae"></a>

### Images


<a id="org6a3b711"></a>

### Schematic

[./hardware/fly\_bowl\_wiring/schematic/fly\_bowl\_wiring.pdf](./hardware/fly_bowl_wiring/schematic/fly_bowl_wiring.pdf)

![img](./images/fly_bowl_wiring/schematic/images/schematic00.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic01.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic02.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic03.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic04.png)


<a id="org2e8f92c"></a>

### Gerbers


<a id="org378a925"></a>

### Bill of Materials

1.  PCB Parts

    |    |
    |--- |
    |  |

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


<a id="org6a994d0"></a>

### Supplemental Documentation

1.  Assembly Instructions


<a id="orgf8aa930"></a>

# Firmware


<a id="org07c5628"></a>

## FlyBowlController


<a id="orgeeb161b"></a>

### Library Information

-   **Name:** FlyBowlController
-   **Version:** 1.0.0
-   **License:** BSD
-   **URL:** <https://github.com/janelia-arduino/FlyBowlController>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    Modular device fly bowl controller library.


<a id="org03e97ab"></a>

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
      "step_duration"
    ],
    "properties": [
      "flyBowlsEnabled",
      "experimentDelay"
    ],
    "callbacks": [
      "setIrBacklightsOn",
      "setIrBacklightsOff",
      "setVisibleBacklightsOn",
      "setVisibleBacklightsOff",
      "removeAllExperimentSteps",
      "runExperiment",
      "stopExperiment"
    ]
  }
}
```


<a id="org51a8f4f"></a>

### API GENERAL

<./firmware/FlyBowlController/api/>


<a id="org869aa89"></a>

### Ancestors

<https://github.com/janelia-arduino/ModularServer>

<https://github.com/janelia-arduino/ModularDeviceBase>

<https://github.com/janelia-arduino/DigitalController>

<https://github.com/janelia-arduino/BacklightController>


<a id="org0ac8120"></a>

### Clients


<a id="orge2642b2"></a>

### Devices

<https://github.com/janelia-modular-devices/modular_device_base>

<https://github.com/janelia-modular-devices/backlight_controller>

<https://github.com/janelia-modular-devices/fly_bowl_controller>


<a id="orgf8bb024"></a>

### More Detailed Modular Device Information

<https://github.com/janelia-modular-devices/modular-devices>


<a id="org6cb8631"></a>

### Installation Instructions

<https://github.com/janelia-arduino/arduino-libraries>
