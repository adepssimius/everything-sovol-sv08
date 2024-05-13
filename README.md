# Everything Sovol SV08

A place to store the knowledge I have found about the SV08.

Heavily inspired by the work of bassamanator's excellent [everything-sovol-sv06 repo](https://github.com/bassamanator/everything-sovol-sv06). I could not have been succesful with my SV06 without it.

You can contribute by making a [pull-request](https://github.com/adepssimius/everything-sovol-sv08/pulls), creating an [issue](https://github.com/adepssimius/everything-sovol-sv08/issues), or starting a [discussion](https://github.com/adepssimius/everything-sovol-sv08/discussions).

_None of the links found here are affiliate links._

For now I am using this as an outline to plan and a place to catalog mods that I find.

# Shipping Status
None reported shipped currently.

# Outline

1. Printed Upgrades
    1. [Alternative More Printable SV08 Toolhead Cover by ectoBRUH](#more-printable-sv08-toolhead-cover-by-ectobruh)
    2. [BTT 5" HDMI Screen Adapter by Nadir](#btt-5-hdmi-screen-adapter-by-nadir)
    3. [Inductive Probe Elimination](#inductive-probe-elimination)
        1. [Microprobe Mod by Nixz_Leon](#microprobe-mod-by-nixz_leon)
        2. [Klicky Probe Mod by Nadir](#klicky-probe-mod-by-nadir)
    4. [Printable Belt Mounts by EctoBRUH](#printable-belt-mounts-by-ectobruh)
2. Modifications
    1. [Cheaper HDMI Touchscreen](#cheaper-hdmi-touchscreen)
    2. [Quieter Mainboard Fan](#quieter-mainboard-fan)
3. [Support Me ❤️](#support-me)
4. [Stay Up-to-Date](#stay-up-to-date)
5. [Reviews](#reviews)
6. [Links](#links)


# Printed Upgrades

## More Printable SV08 Toolhead Cover by ectoBRUH
The printhead cover is not well suited to printing. Print your own more easily with this model.

#### Testing Status: ❓ Untested

#### Available at
- [Printables](https://www.printables.com/model/850271-sovol-sv08-alternative-toolhead-cover)
- [Thingiverse](https://www.thingiverse.com/thing:6588417)

## BTT 5" HDMI Screen Adapter by Nadir
The screen available from sovol is a bit pricey for what it is. Use this to be able to use a common 3d printer touch screen and have it look like your printer came with it.

#### Testing Status: ❓ Untested

#### Available at
- [Printables](https://www.printables.com/model/848629-sovol-sv08-5-btt-hdmi-dislay)

#### Other info
- [5" BTT Screen on aliexpress](https://www.aliexpress.us/item/3256805702942821.html)
- [5" BTT Screen on Amazon](https://www.amazon.com/BIGTREETECH-Display-800x480-Compatible-Raspberry/dp/B0BC4CPDC3)
- [Reddit discussion](https://www.reddit.com/r/Sovol/comments/1c7dpnz/hello_everyone_here_its_my_first_mod_to_the_sv08/)

## Inductive Probe Elimination
Using an inductive probe to find your z location can be problematic due to temperature induced error. If you home with a cold probe, you will get a different measurement compared to if the probe has been sitting over a heated bed for a while. Using a physical probe to touch the bed eliminates this temperature drift.

## Microprobe Mod by Nixz_Leon
This is apparently designed for a "Biqu Microprobe"

#### Testing Status: ❓ Untested

#### Available at
- [Printables](https://www.printables.com/model/848561-sv08-microprobe-mod)

## Klicky Probe Mod by Nadir
A Klicky probe is picked up by the printhead to be used for leveling then put back in a holder before printing. Klicky probes are typical on Voron 2.4 printers and ensure that you will get repeatable measurements on both a cold start and after hours of printing.

_Further instructions will be added soon, as this is one of the first mods I wil be doing to my SV08._

#### Testing Status: ❓ Untested

#### Available at
- [Printables](https://www.printables.com/model/849409-klicky-probe-for-sovol-sv08-abl)

#### Other Info
- [Reddit Discussion and more info](https://www.reddit.com/r/Sovol/comments/1c82929/klicky_probe_mod_for_sovol_sv08/)

## Printable Belt Mounts by ectoBRUH
These are the belt mounts that are included with the printer, modified to be more easily printable.

#### Testing Status: ❓ Untested

#### Available at
- [Printables](https://www.printables.com/model/851693)
- [Thingiverse](https://www.thingiverse.com/thing:6588421)

# Modifications

## Cheaper HDMI Touchscreen
The screen price from sovol is pretty steep. Here's a few HDMI touchscreens that should work just fine. See the [5" HDMI Screen Adapter](#btt-5-hdmi-screen-adapter-by-nadir) as well.

- [5" BTT on aliexpress](https://www.aliexpress.us/item/3256805702942821.html) - ❓ Untested
- [5" BTT on Amazon](https://www.amazon.com/BIGTREETECH-Display-800x480-Compatible-Raspberry/dp/B0BC4CPDC3) - ❓ Untested
- [Generic 7" with integrated stand on aliexpress](https://www.aliexpress.us/item/3256805771551994.html) - ❓ Untested

## Quieter Mainboard Fan
The mainboard fan is a 24V 4010 axial fan. It can be replaced with a similar fan.

#### Testing Status: ❓ Tested by community, not by me.

#### Software Modification
By DonutCables - [reddit thread here](https://www.reddit.com/r/Sovol/comments/1cqntzu/first_mod_on_my_sv08_noctua_fan_for_the/), GH Issue with detail [here](https://github.com/adepssimius/everything-sovol-sv08/issues/3)

This can be used with any of the fans, but a quieter fan will still be best. Adding this code to your `printer.cfg` should set the fan to only run while the controller is hot. This won't make the fan quieter while it is running, but it will allow it to not run all the time.

```
[temperature_fan MCU_fan]
pin: PA1
max_power: 1.0
shutdown_speed: 1.0
kick_start_time: 0.5
off_below: 0.05
sensor_type: temperature_host
control: watermark
target_temp: 45
min_temp: 15
max_temp: 80
max_speed: 1.0
min_speed: 0.0
```

You'll need to comment out the `[temperature_sensor Host_temp]` section and the `[output_pin *]` section for the PA1 pin that the fan is using by default.


#### Testing Status: ❓ Tested by community, not by me.

#### Noctua Fan
A [24V 4010 Noctua fan](https://www.amazon.com/Noctua-NF-A4x10-24V-PWM-Applications/dp/B0CN39MCPL) will also work directly without the buck converter. It is currently not available on amazon. This is confirmed to work [here](https://www.reddit.com/r/Sovol/comments/1cqntzu/first_mod_on_my_sv08_noctua_fan_for_the/) and with more detail [here].

A [12V 4010 Noctua fan](https://www.amazon.com/Noctua-Cooling-Blades-Bearing-NF-A4x10/dp/B009NQLT0M) has been succesfully used with a [LM2596S DC-DC Buck Converter](https://www.amazon.com/LM2596-Converter-Module-Supply-1-23V-30V/dp/B008BHBEE0) inside a [3d printed case](https://www.printables.com/model/64519-dc-dc-buck-converter-case-lm2596). The yellow wire on the noctua fan was clipped and the black and red wires used to power the fan. This is community tested.

# Support Me

Please ⭐ star this repository!

Support the authors of the individual mods, [open source](https://en.wikipedia.org/wiki/Open_source), and donate to [FIRST Robotics](https://www.firstinspires.org/donate), which provides kids with an opportunity to learn about Science, Technology, Engineering, and Math.

# Stay Up-to-Date

This repository is a work in progress. Watch for updates by starring this repo.

# Reviews
Here are the reviews and hands on videos of the SV08 that I have found so far in case you are trying to make a decision on purchasing.

- [gerGO PRINT 3D - 16:13](https://www.youtube.com/watch?v=oP_1vLehiww) is not a hands on or a review, but rather a meta-review that includes clips from many of the other videos listed here.
- [mpoxDE - 43:09](https://www.youtube.com/watch?v=BmYEP9sSOzg) is a german language review that probably has some of the best analysis of the printer. Auto caption translation will be your friend.
- [My Tech Fun - 25:28](https://www.youtube.com/watch?v=iqZD7Zr2Hwg) has some excellent real worls usage and characterization test prints with bed levelling and flow rate analysis. He demonstrates time lapses with the built in camera.
- [The Next Layer - 28:15](https://www.youtube.com/watch?v=PlFH9bzdwQs) is sponsored by Sovol.
- [Loyal Moses - 18:44](https://www.youtube.com/watch?v=nxSXFJDDjR8)
- [The Edge of Tech - 16:45](https://www.youtube.com/watch?v=1IAu-89P8TE)
- [Nathan Builds Robots - 23:08](https://www.youtube.com/watch?v=Nc3oLzftmoo)
- [Nero3D's Unboxing and first prints livestream - 3:05:06](https://www.youtube.com/watch?v=O1DSXK5TmKE)
- [Nero3D's "not a review" - 15:29](https://www.youtube.com/watch?v=BpxruCuhfuc) is an unscripted list of complaints.
- [Aurora Tech's Sovol SV08 Review - 26:13](https://www.youtube.com/watch?v=OgX14lbYAJw)

# Links

## Useful Resources

- ⭐⭐⭐⭐⭐ [Ellis' Print Tuning Guide](https://ellis3dp.com/Print-Tuning-Guide)
- [Simplify3D Print Quality Troubleshooting Guide](https://www.simplify3d.com/resources/print-quality-troubleshooting/)

## Sovol Official Links

- [SV08 Stock Controller Home Directory](https://github.com/Sovol3d/SV08/tree/main/home)
- [SV08 Controller Installation, Specifications, and Models](https://github.com/Sovol3d/SV08)
- [SV08 Launch Live Stream](https://www.youtube.com/watch?v=BVQbmPFRowE)
- [SV08 Launch Live Stream Part 2](https://www.youtube.com/watch?v=fEe7nXkIw5E)
- [SV08 Q&A](https://www.youtube.com/watch?v=yZcEnbXUJvI)
