## Why we need ESS/Dynamic ESS on Victron?

My goal was to decrease load to the grid system during the blackouts in Ukraine. Dynamic ESS mode allowing working from battery during certain period of the day and charge during the night. This feature is enabled by default.

If you use Victron Multiplus/Quatro inverter along with Pylontech battery, this manual could help you.

## Preparation

1. Your system should have CerboGX device and configured VRM. Otherwise, you need to use Vicrton [MK3 upgrade cable](https://www.victronenergy.com/accessories/interface-mk3-usb).

2. You need a laptop with Windows and install [VeConfigure](https://www.victronenergy.com/Executables/VEConfig/VECSetup_A.exe) software on it.

3. Be ready that on some stages the power of your appartment could be off. Internet could also be off. Be ready for that. It should not be for too long.

## Update

1. Got to your VRM and export current config from your inverter. VRM -> Device List -> Remote VEConfigure -> Download
![ess setup1](https://github.com/anpolimus/smarthome_docs/blob/main/victron/enable_ess/ess_setup_1.png)

2. Open your inverter's config using VEConfigure3 software on Windows and disable Virtual Switch (without this step, you cant add any of Assistants)
![ess_setup2](/victron/enable_ess/ess_2.png)

3. Add new Assitant (Select ESS in the list).
!(/victron/enable_ess/ess_3.png)

4. Select battery type.
!(/victron/enable_ess/ess_4.png)

Here is the summary from Victron's manual, related to the pylontech battery.

```
ESS System Settings
If you are using the battery as part of a grid connected ESS system, please review the ESS Quickstart guide and Design and Installation Manual.
The settings that are specific to the Pylontech battery in the VEConfigure ESS Assistant are below:
Select the externally managed Lithium battery option

ESS Parameter	Settings
Sustain voltage.	48V
Dynamic cut-off values	set all values to 46V.
Restart offset:	1.2V (Default)
Due to the reliability of the grid supply and the behaviour of the sustain voltage threshold in ESS; you may wish to suppress the low voltage pre-alarm warning so that it does not trigger every day on its regular deep cycle. See ESS FAQ Q5 - about suppressing the low-voltage alarm.
```

5. Select sustain voltage as 48V and all dynamic cut off voltages as 46V

6. Once you've verified and checked your new configuration, you could update your original config file. You can do it by trying to close VeConfigure and saving config on exit. Please do not save config as separate file, bc it would save file to the wrong file type that VRM cant use as input config. You should also set your country on the Grid tab of the VeConfigure 3.

7. Now we are ready to upload our updated config to the inverter with help of VRM. Use upload button for that.
!(/victron/enable_ess/ess_5.png)

8. During configuration update inverter would shut down for a sec and you could loose your power for some time. Dont worry, it is only for a couple of seconds.

9. If everything is fine, you could see new option in the VRM, saying that you now have access to the ESS configuration.

!(/victron/enable_ess/ess_6.png)
!(/victron/enable_ess/ess_7.png)
