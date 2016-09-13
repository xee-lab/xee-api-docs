# Signals list

All the *signals* you can access via the [signals API](signals.md)

> All the *signals* ending by `Sts` are *status signals*, it means that their value is `0` or `1` like `booleans`

## Standard Signals

> See the human readable list in [https://dev.xee.com/signals](https://dev.xee.com/signals)
> 
> The list here represents the *Standard Signals*

|Signal name|Signal description|Comment|
|---|---|---|
|**_XeeCONNECT_**|||
|`BatteryVoltage`|Represents the **Battery Voltage** value|Value is in `V`|
|**_Lights_**|||
|`FrontFogLightSts`|Represents the **Front fog lights** status|`0` = `off`,<br /> `1` = `on`|
|`RearFogLightSts`|Represents the **Rear fog lights** status|`0` = `off`,<br /> `1` = `on`|
|`HazardSts`|Represents the **Warnings** status|`0` = `off`,<br /> `1` = `on`|
|`HeadLightSts`|Represents the **Head Lights** status|`0` = `off`,<br /> `1` = `on`|
|`HighBeamSts`|Represents the **High Beams** status|`0` = `off`,<br /> `1` = `on`| 
|`LowBeamSts`|Represents the **Low Beams** status|`0` = `off`,<br /> `1` = `on`| 
|`LeftIndicatorSts`|Represents the **Left indicator** status|`0` = `off`,<br /> `1` = `on`|
|`RightIndicatorSts`|Represents the **Right indicator** status|`0` = `off`,<br /> `1` = `on`|
|**_Misc_**|||
|`FuelLevel`|Represents the amout of **Fuel** in the tank|Value is in `L`|
|`IgnitionSts`|Represents the **Ignition** status|`0` = `off`,<br /> `1` = `on`|
|`Odometer`|Represents the **Odometer** value|Value is in `km`|
|`LockSts`|Represents the **Lock** status of the car|`0` = `unlocked`,<br /> `1` = `locked`|
|**_Wipers_**|||
|`IntermittentWiperSts`|Represents the **Intermittent Wipers** status|`0` = `off`,<br /> `1` = `on`|
|`ManualWiperSts`|Represents the **Manual Wipers** status|`0` = `off`,<br /> `1` = `on`|
|`LowSpeedWiperSts`|Represents the **Low speed Wipers** status|`0` = `off`,<br /> `1` = `on`|
|`HighSpeedWiperSts`|Represents the **High speed Wipers** status|`0` = `off`,<br /> `1` = `on`|
|`AutoRearWiperSts`|Represents the **Auto rear Wipers** status|`0` = `off`,<br /> `1` = `on`|
|`ManualRearWiperSts`|Represents the **Manual rear Wiper** status|`0` = `off`,<br /> `1` = `on`|
|**_Speed_**|||
|`EngineSpeed`|Represents the **Engine speed**|Value is in `rpm`|
|`VehiculeSpeed`|Represents the **Vehicle speed**|Value is in `km/h`|

## Advanced Signals

> See the human readable list in [https://dev.xee.com/signals](https://dev.xee.com/signals)
> 
> The list here represents the *Advanced Signals*, note that **THEY ARE NOT AVAILABLE BY DEFAULT**

|Signal name|Signal description|Comment|
|---|---|---|
|**_Air Conditioning_**|||
|`AirCondSwitchSts`|Represents the **Air conditioning** status|`0` = `off`,<br /> `1` = `on`|
|`CoolantPressure`|Represents the **Coolant Pressure**|Value is in `bar`|
|`OutdoorTemp`|Represents the **Outdoor temperature**|Value is in `° C`|
|`VentilationSts`|Represents the **Ventilation** status |`0` = `off`,<br /> `1` = `on`|
|**_Binnacle_**|||
|`CruiseControlSts`|Represents the **Cruise control** status|`0` = `off`,<br /> `1` = `on`|
|`KeySts`|Represents the **Key presence** status|`0` = `absent`,<br /> `1` = `present`|
|`ReverseGearSts`|Represents the **Reverse Gear** status |`0` = `off`,<br /> `1` = `on`|
|**_Doors and Caps_**|||
|`FrontLeftDoorSts`|Represents the **Front left door** status |`0` = `closed`,<br /> `1` = `open`|
|`HoodSts`|Represents the **Hood** status |`0` = `closed`,<br /> `1` = `open`|
|`FrontRightDoorSts`|Represents the **Front right door** status |`0` = `closed`,<br /> `1` = `open`|
|`RearLeftDoorSts`|Represents the **Rear Left door** status |`0` = `closed `,<br /> `1` = `open`|
|`RearRightDoorSts`|Represents the **Rear Right door** status |`0` = `closed`,<br /> `1` = `open`|
|`TrunkSts`|Represents the **Trunk** status |`0` = `closed`,<br /> `1` = `open`|
|**_Pedals_**|||
|`BrakePedalSts`|Represents the **Brake Pedal** status |`0` = `released`,<br /> `1` = `pressed`|
|`BrakePedalPosition`|Represents the **Brake Pedal** position|Value is in `%` <br />(*0%* = *released*, *100%* = *fully pressed*)|
|`ClutchPedalSts`|Represents the **Clutch Pedal** status |`0` = `released`,<br /> `1` = `pressed`|
|`ClutchPedalPosition`|Represents the **Clutch Pedal** position |Value is in `%` <br />(*0%* = *released*, *100%* = *fully pressed*)|
|`HandBrakeSts`|Represents the **Hand Brake** status|`0` = `released`,<br /> `1` = `engaged`|
|`ThrottlePedalSts`|Represents the **Throttle Pedal** status |`0` = `released`,<br /> `1` = `pressed` <br />(*0%* = *released*, *100%* = *fully pressed*)|
|`ThrottlePedalPosition`|Represents the **Throttle Pedal** position |Value is in `%` <br />(*0%* = *released*, *100%* =  *fully pressed*)|
|**_Safety_**|||
|`FrontLeftSeatBeltSts`|Represents the **Front Left Seat belt** status |`0` = `unfasten`,<br /> `1` = `fasten`|
|`FrontRightSeatBeltSts`|Represents the **Front Right seat belt** status |`0` = `unfasten`,<br /> `1` = `fasten`|
|`PassAirbagSts`|Represents the **Passenger's Airbag** status |`0` = `activated`,<br /> `1` = `disabled`|
|**_Steering Wheel_**|||
|`SteeringWheelAngle`|Represents the **Steering Wheel Angle** |Value is in `°` <br />(from *0°* to *???°* depends on vehicle)|
|`SteeringWheelSide`|Represents the **Steering Wheel Side** |`0` = `left`,<br /> `1` = `right`|
|**_Windows_**|||
|`FrontLeftWindowSts`|Represents the **Front Left Window** status |`0` = `closed`,<br /> `1` = `open`|
|`FrontLeftWindowPosition`|Represents the **Front Left Window** position |Value is in `%` <br />(of opening *0%* =  *closed*, *100%* = *fully open*)|
|`FrontRightWindowSts`|Represents the **Front Right Window** status |`0` = `closed `,<br /> `1` = `closed`|
|`FrontRightWindowPosition`|Represents the **Front Right Window** position |Value is in `%` <br />(of opening *0%* =  *closed*, *100%* = *fully open*)|
|`RearLeftWindowSts`|Represents the **Rear Left Window** status |`0` = `closed`,<br /> `1` = `open`|
|`RearLeftWindowPosition`|Represents the **Rear Left Window** position |Value is in `%` <br />(of opening *0%* =  *closed*, *100%* = *fully open*)|
|`RearRightWindowSts`|Represents the **Rear Right Window** status |`0` = `closed`,<br /> `1` = `open`|
|`RearRightWindowPosition`|Represents the **Rear Right Window** position |Value is in `%` <br />(of opening *0%* =  *closed*, *100%* = *fully open*)|
|`WindowsLockSts`|Represents the **Windows Lock** status |`0` = `released`,<br /> `1` = `locked`|
|**_Speed_**|||
|`FrontLeftWheelSpeed`|Represents the **Front Left Wheel** speed |Value is in `km/h`|
|`FrontRightWheelSpeed `|Represents the **Front Right Wheel** speed |Value is in `km/h`|
|`RearLeftWheelSpeed `|Represents the **Rear Left Wheel** speed |Value is in `km/h`|
|`RearRightWheelSpeed `|Represents the **Rear Right Wheel** speed |Value is in `km/h`|
