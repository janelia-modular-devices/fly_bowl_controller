- [Repository Information](#org78dec60)
  - [Description](#org1b867b1)
- [Images](#orgef663e2)
- [Usage Instructions](#org294524a)
  - [Example Code](#org19bb072)
    - [Arduino Serial Monitor](#orgaa4314a)
    - [Python](#orgcb3712e)
    - [Matlab](#org58f7152)
  - [Example Experiment Step Waveform](#orgf88357a)
    - [Step Duration](#orga1e1b4a)
    - [Step Delay](#org6b1ed55)
    - [Sequence Count](#orgf7dce52)
    - [Sequence Off Duration](#org4363bfc)
    - [Pulse Count](#orgfdfb6c8)
    - [Pulse On Duration](#org8048e3e)
    - [Pulse Period](#orgaa62b41)
    - [Intensity](#org40f1779)
- [Build Instructions](#orgd14d0b7)
- [Hardware](#org7d3a58a)
  - [backlight\_controller\_5x3](#org274f4fa)
    - [Repository Information](#org5b84bed)
    - [Images](#org64d9994)
    - [Schematic](#org7ace527)
    - [Gerbers](#org9074de8)
    - [Bill of Materials](#org689833d)
    - [Supplemental Documentation](#orgfe415a2)
  - [fly\_bowl\_wiring](#orgff2a422)
    - [Repository Information](#org4991a2a)
    - [Images](#org8978c75)
    - [Schematic](#org1288f90)
    - [Gerbers](#org4d43f06)
    - [Bill of Materials](#orge7ced06)
    - [Supplemental Documentation](#org9e8ddf4)
- [Firmware](#org33ccd7a)
  - [FlyBowlController](#org976de2d)
    - [Library Information](#org20ad6a9)
    - [API NAMES](#orgf4c3ed2)
    - [API GENERAL](#org812c232)
    - [Ancestors](#org11e91d2)
    - [Clients](#org1a72cbe)
    - [Devices](#org0297529)
    - [More Detailed Modular Device Information](#org28df6f9)
    - [Installation Instructions](#orge2eccf8)



<a id="org78dec60"></a>

# Repository Information

-   **Name:** fly\_bowl\_controller
-   **Version:** 2.0
-   **License:** BSD, Open-Source Hardware
-   **URL:** <https://github.com/janelia-modular-devices/fly_bowl_controller>
-   **Author:** Peter Polidoro
-   **Email:** peter@polidoro.io


<a id="org1b867b1"></a>

## Description

This device controls the IR and visible backlights in the fly bowl rig along with the backlight cooling fans and indicator lights.


<a id="orgef663e2"></a>

# Images

![img](./images/front_top.png)

![img](./images/top_bowls.png)

![img](./images/wired.png)


<a id="org294524a"></a>

# Usage Instructions


<a id="org19bb072"></a>

## Example Code


<a id="orgaa4314a"></a>

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
#         "setIrBacklightsAndFansOnAtPower",
#         "setIrBacklightsAndFansOnAtIntensity",
#         "setVisibleBacklightsAndIndicatorsOnAtPower",
#         "setVisibleBacklightsAndIndicatorsOnAtIntensity",
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
#         "setIrBacklightsAndFansOn",
#         "setIrBacklightsAndFansOff",
#         "setVisibleBacklightsAndIndicatorsOn",
#         "setVisibleBacklightsAndIndicatorsOff",
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
irBacklightPowerToIntensityRatio setValue [5.99,5.59,5.41,5.57]
# {
#   "id": "irBacklightPowerToIntensityRatio",
#   "result": [
#     5.990000,
#     5.590000,
#     5.410000,
#     5.570000
#   ]
# }
visibleBacklightPowerToIntensityRatio setValue [14.66,15.87,14.04,14.77]
# {
#   "id": "visibleBacklightPowerToIntensityRatio",
#   "result": [
#     14.660000,
#     15.870000,
#     14.040000,
#     14.770000
#   ]
# }
setIrBacklightsAndFansOnAtIntensity 4.5
# {
#   "id": "setIrBacklightsAndFansOnAtIntensity",
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
#       "intensity",
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
addExperimentStep 1.71 100 50 5 750 4 1.0 6.0
# {
#   "id": "addExperimentStep",
#   "result": 0
# }
addExperimentStep 2.7 100 50 35 2500 4 0.0 20.0
# {
#   "id": "addExperimentStep",
#   "result": 1
# }
getExperimentSteps
# {
#   "id": "getExperimentSteps",
#   "result": [
#     {
#       "intensity": 1.710000,
#       "pulse_period": 100,
#       "pulse_on_duration": 50,
#       "pulse_count": 5,
#       "sequence_off_duration": 750,
#       "sequence_count": 4,
#       "step_delay": 1.000000,
#       "step_duration": 6.000000
#     },
#     {
#       "intensity": 2.700000,
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
setVisibleBacklightsAndIndicatorsOnAtIntensity 4.6
# {
#   "id": "setVisibleBacklightsAndIndicatorsOnAtIntensity",
#   "result": null
# }
setVisibleBacklightsAndIndicatorsOff
# {
#   "id": "setVisibleBacklightsAndIndicatorsOff",
#   "result": null
# }
addVisibleBacklightsPwm ?
# {
#   "id": "addVisibleBacklightsPwm",
#   "result": {
#     "name": "addVisibleBacklightsPwm",
#     "firmware": "FlyBowlController",
#     "parameters": [
#       "intensity",
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
addVisibleBacklightsPwm 6.0 5000 100 50 1000
# {
#   "id": "addVisibleBacklightsPwm",
#   "result": 0
# }
stopPwm 0
# {
#   "id": "stopPwm",
#   "result": null
# }
setIrBacklightsAndFansOff
# {
#   "id": "setIrBacklightsAndFansOff",
#   "result": null
# }
```


<a id="orgcb3712e"></a>

### Python

```python
from modular_client import ModularClient
dev = ModularClient(timeout=0.1) # Automatically finds device if one available
dev.get_device_id()
# {'name': 'fly_bowl_controller', 'form_factor': '5x3', 'serial_number': 0}
dev.set_properties_to_defaults(['ALL'])
dev.fly_bowls_enabled('getValue')
# [True, True, True, True]
dev.fly_bowls_enabled('setValue',[True,False,True,False])
# [True, False, True, False]
dev.ir_backlight_power_to_intensity_ratio('setValue',[5.99,5.59,5.41,5.57])
# [5.99, 5.59, 5.41, 5.57]
dev.visible_backlight_power_to_intensity_ratio('setValue',[14.66,15.87,14.04,14.77])
# [14.66, 15.87, 14.04, 14.77]
dev.set_ir_backlights_and_fans_on_at_intensity(4.5) # 4.5 mW/mm^2
dev.remove_all_experiment_steps()
intensity = 1.71 # 1.71 mW/mm^2
pulse_period = 100 # 100 ms
pulse_on_duration = 50 # 50 ms
pulse_count = 5
sequence_off_duration = 750 # 750 ms
sequence_count = 4
step_delay = 1.0 # 1.0 s
step_duration = 6.0 # 6.0 s
dev.add_experiment_step(intensity,
                        pulse_period,
                        pulse_on_duration,
                        pulse_count,
                        sequence_off_duration,
                        sequence_count,
                        step_delay,
                        step_duration)
# 0
intensity = 2.7 # 2.7 mW/mm^2
pulse_period = 100 # 100 ms
pulse_on_duration = 50 # 50 ms
pulse_count = 35
sequence_off_duration = 2500 # 2500 ms
sequence_count = 4
step_delay = 0.0 # 0.0 s
step_duration = 20.0 # 20.0 s
dev.add_experiment_step(intensity,
                        pulse_period,
                        pulse_on_duration,
                        pulse_count,
                        sequence_off_duration,
                        sequence_count,
                        step_delay,
                        step_duration)
# 1
dev.get_experiment_steps()
# [{'intensity': 1.71,
#   'pulse_period': 100,
#   'pulse_on_duration': 50,
#   'pulse_count': 5,
#   'sequence_off_duration': 750,
#   'sequence_count': 4,
#   'step_delay': 1.0,
#   'step_duration': 6.0},
#  {'intensity': 2.7,
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
dev.set_visible_backlights_and_indicators_on_at_intensity(4.6) # 4.6 mW/mm^2
dev.set_visible_backlights_and_indicators_off()
dev.add_visible_backlights_pwm('?')
# {'name': 'addVisibleBacklightsPwm',
#  'firmware': 'FlyBowlController',
#  'parameters': ['intensity',
#                 'pulse_delay',
#                 'pulse_period',
#                 'pulse_on_duration',
#                 'pulse_count'],
#  'result_info': {'type': 'long'}}
intensity = 6.0 # 6.0 mW/mm^2
pulse_delay = 1000 # 1000 ms
pulse_period = 100 # 100 ms
pulse_on_duration = 50 # 50 ms
pulse_count = 1000
pwm_index = dev.add_visible_backlights_pwm(intensity,
                                           pulse_delay,
                                           pulse_period,
                                           pulse_on_duration,
                                           pulse_count)
dev.stop_pwm(pwm_index)
dev.set_ir_backlights_and_fans_off()
```


<a id="org58f7152"></a>

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
dev.irBacklightPowerToIntensityRatio('setValue',{5.99,5.59,5.41,5.57})
% [5.99]    [5.59]    [5.41]    [5.57]
dev.visibleBacklightPowerToIntensityRatio('setValue',{14.66,15.87,14.04,14.77})
% [14.66]    [15.87]    [14.04]    [14.77]
dev.setIrBacklightsAndFansOnAtIntensity(4.5); % 4.5 mW/mm^2
dev.removeAllExperimentSteps();
intensity = 1.71; % 1.71 mW/mm^2
pulse_period = 100; % 100 ms
pulse_on_duration = 50; % 50 ms
pulse_count = 5;
sequence_off_duration = 750; % 750 ms
sequence_count = 4;
step_delay = 1.0; % 1.0 s
step_duration = 6.0; % 6.0 s
dev.addExperimentStep(intensity, ...
                      pulse_period, ...
                      pulse_on_duration, ...
                      pulse_count, ...
                      sequence_off_duration, ...
                      sequence_count, ...
                      step_delay, ...
                      step_duration)
% 0
intensity = 2.7; % 2.7 mW/mm^2
pulse_period = 100; % 100 ms
pulse_on_duration = 50; % 50 ms
pulse_count = 35;
sequence_off_duration = 2500; % 2500 ms
sequence_count = 4;
step_delay = 0.0; % 0.0 s
step_duration = 20.0; % 20.0 s
dev.addExperimentStep(intensity, ...
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
%             intensity: 1.71
%          pulse_period: 100
%     pulse_on_duration: 50
%           pulse_count: 5
% sequence_off_duration: 750
%        sequence_count: 4
%            step_delay: 1
%         step_duration: 6
experiment_steps{2}
%             intensity: 2.7
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
dev.setVisibleBacklightsAndIndicatorsOnAtIntensity(4.6); % 4.6 mW/mm^2
dev.setVisibleBacklightsAndIndicatorsOff();
intensity = 6.0; % 6.0 mW/mm^2
pulse_delay = 1000; % 1000 ms
pulse_period = 100; % 100 ms
pulse_on_duration = 50; % 50 ms
pulse_count = 1000;
pwm_index = dev.addVisibleBacklightsPwm(intensity, ...
                                        pulse_delay, ...
                                        pulse_period, ...
                                        pulse_on_duration, ...
                                        pulse_count);
dev.stopPwm(pwm_index);
dev.setIrBacklightsAndFansOff();
dev.close();
clear dev;
```


<a id="orgf88357a"></a>

## Example Experiment Step Waveform

Yellow waveform shows visible backlight.

Blue waveform shows visible backlight indicator LED.


<a id="orga1e1b4a"></a>

### Step Duration

step\_duration = 6.0 s

![img](./images/waveform/step_duration.png)


<a id="org6b1ed55"></a>

### Step Delay

step\_delay = 1.0 s

![img](./images/waveform/step_delay.png)


<a id="orgf7dce52"></a>

### Sequence Count

sequence\_count = 4

![img](./images/waveform/sequence_count.png)


<a id="org4363bfc"></a>

### Sequence Off Duration

sequence\_off\_duration = 750 ms

![img](./images/waveform/sequence_off_duration.png)


<a id="orgfdfb6c8"></a>

### Pulse Count

pulse\_count = 5

![img](./images/waveform/pulse_count.png)


<a id="org8048e3e"></a>

### Pulse On Duration

pulse\_on\_duration = 50 ms

![img](./images/waveform/pulse_on_duration.png)


<a id="orgaa62b41"></a>

### Pulse Period

pulse\_period = 100 ms

![img](./images/waveform/pulse_period.png)


<a id="org40f1779"></a>

### Intensity

intensity = 1.71 mW/mm^2 (power = 25 %)

![img](./images/waveform/intensity.png)


<a id="orgd14d0b7"></a>

# Build Instructions


<a id="org7d3a58a"></a>

# Hardware


<a id="org274f4fa"></a>

## backlight\_controller\_5x3


<a id="org5b84bed"></a>

### Repository Information

-   **Name:** backlight\_controller\_5x3
-   **Version:** 1.2
-   **License:** Open-Source Hardware
-   **URL:** <https://github.com/janelia-kicad/backlight_controller_5x3>
-   **Author:** Peter Polidoro
-   **Email:** peter@polidoro.io

1.  Description

    This board controls up to four Smart Vision backlights with IR and visible channels plus additional high and low power channel outputs.


<a id="org64d9994"></a>

### Images

![img](./images/backlight_controller_5x3/images/top.png)

![img](./images/backlight_controller_5x3/images/bottom.png)


<a id="org7ace527"></a>

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


<a id="org9074de8"></a>

### Gerbers

Send gerbers zip file to your favorite PCB manufacturer for fabrication.

[./hardware/backlight\_controller\_5x3/gerbers/backlight\_controller\_5x3\_v1.2.zip](./hardware/backlight_controller_5x3/gerbers/backlight_controller_5x3_v1.2.zip)

![img](./images/backlight_controller_5x3/gerbers/images/gerbers00.png)

![img](./images/backlight_controller_5x3/gerbers/images/gerbers01.png)


<a id="org689833d"></a>

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


<a id="orgfe415a2"></a>

### Supplemental Documentation

1.  Assembly Instructions

    -   Solder surface mount and through hole components onto the pcb.


<a id="orgff2a422"></a>

## fly\_bowl\_wiring


<a id="org4991a2a"></a>

### Repository Information

-   **Name:** fly\_bowl\_wiring
-   **Version:** 1.0
-   **License:** Open-Source Hardware
-   **URL:** <https://github.com/janelia-kicad/fly_bowl_wiring>
-   **Author:** Peter Polidoro
-   **Email:** peter@polidoro.io

1.  Description

    Wiring schematics and documentation for the multiple fly bowl rig.


<a id="org8978c75"></a>

### Images

![img](./images/fly_bowl_wiring/images/top.png)


<a id="org1288f90"></a>

### Schematic

[./hardware/fly\_bowl\_wiring/schematic/fly\_bowl\_wiring.pdf](./hardware/fly_bowl_wiring/schematic/fly_bowl_wiring.pdf)

![img](./images/fly_bowl_wiring/schematic/images/schematic00.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic01.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic02.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic03.png)

![img](./images/fly_bowl_wiring/schematic/images/schematic04.png)


<a id="org4d43f06"></a>

### Gerbers


<a id="orge7ced06"></a>

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


<a id="org9e8ddf4"></a>

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


<a id="org33ccd7a"></a>

# Firmware


<a id="org976de2d"></a>

## FlyBowlController


<a id="org20ad6a9"></a>

### Library Information

-   **Name:** FlyBowlController
-   **Version:** 3.0.0
-   **License:** BSD
-   **URL:** <https://github.com/janelia-arduino/FlyBowlController>
-   **Author:** Peter Polidoro
-   **Email:** peter@polidoro.io

1.  Description

    Modular device fly bowl controller library.


<a id="orgf4c3ed2"></a>

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
      "setIrBacklightsAndFansOnAtPower",
      "setIrBacklightsAndFansOnAtIntensity",
      "setVisibleBacklightsAndIndicatorsOnAtPower",
      "setVisibleBacklightsAndIndicatorsOnAtIntensity",
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
      "setIrBacklightsAndFansOn",
      "setIrBacklightsAndFansOff",
      "toggleIrBacklightsAndFans",
      "setVisibleBacklightsAndIndicatorsOn",
      "setVisibleBacklightsAndIndicatorsOff",
      "toggleVisibleBacklightsAndIndicators",
      "removeAllExperimentSteps",
      "runExperiment",
      "stopExperiment"
    ]
  }
}
```


<a id="org812c232"></a>

### API GENERAL

<./firmware/FlyBowlController/api/>


<a id="org11e91d2"></a>

### Ancestors

<https://github.com/janelia-arduino/ModularServer>

<https://github.com/janelia-arduino/ModularDeviceBase>

<https://github.com/janelia-arduino/DigitalController>

<https://github.com/janelia-arduino/BacklightController>


<a id="org1a72cbe"></a>

### Clients


<a id="org0297529"></a>

### Devices

<https://github.com/janelia-modular-devices/modular_device_base>

<https://github.com/janelia-modular-devices/backlight_controller>

<https://github.com/janelia-modular-devices/fly_bowl_controller>


<a id="org28df6f9"></a>

### More Detailed Modular Device Information

<https://github.com/janelia-modular-devices/modular-devices>


<a id="orge2eccf8"></a>

### Installation Instructions

<https://github.com/janelia-arduino/arduino-libraries>
