# Signals list

All the *signals* you can access via the [signals API](signals.md)

> All the *signals* ending by `Sts` are *status signals*, it means that their value is `0` or `1` like `booleans`

## List

|Signal name|Signal description|Comment|
|---|---|---|
|HighBeamsSts|Represents the High Beams status|`0` if the beams are `off`, `1` if `on`| 
|LowBeamsSts|Represents the Low Beams status|`0` if the beams are `off`, `1` if `on`| 
|HeadLightsSts|Represents the Head Lights status|`0` if the lights are `off`, `1` if `on`|
|HazardSts|Represents the *Warnings* status|`0` if they are `off`, `1` if `on`|
|LeftIndicatorSts|Represents the *left indicator* status|`0` if they are `off`, `1` if `on`|
|RightIndicatorSts|Represents the *right indicator* status|`0` if they are `off`, `1` if `on`|
|FrontFogLightSts|Represents the *front fog lights* status|`0` if they are `off`, `1` if `on`|
|RearFogLightSts|Represents the *rear fog lights* status|`0` if they are `off`, `1` if `on`|
|FuelLevel|Represents the amout of *Fuel* in the tank||
|IgnitionSts|Represents the *Ignition* status|`0` if `off`, `1` if `on`|
|EngineSpeed|Represents the *Engine speed*, as rotations per minutes||
|VehiculeSpeed|Represents the *Vehicle speed*, as `km/h` or other||
|Odometer|Represents the *Odometer* value||
|BatteryVoltage|Represents the *Battery Voltage* value||
|IntermittentWiperSts|Represents the *Intermittent Wiper* status|`0` if they are `off`, `1` if `on`|
|LowSpeedWiperSts|Represents the *Low speed Wiper* status|`0` if they are `off`, `1` if `on`|
|ManualWiperSts|Represents the *Manual Wiper* status|`0` if they are `off`, `1` if `on`|
|HighSpeedWiperSts|Represents the *High speed Wiper* status|`0` if they are `off`, `1` if `on`|
|AutoRearWiperSts|Represents the *Auto rear Wiper* status|`0` if they are `off`, `1` if `on`|
|ManualRearWiperSts|Represents the *Manual rear Wiper* status|`0` if they are `off`, `1` if `on`|
|LockSts|Represents the *Lock* status|`0` if car is `unlocked`, `1` if `locked`|