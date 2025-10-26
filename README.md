
###
Changes made to work with my setup and ESP32-2432S028R



The hardware consists of an ESP32 and an ILI9341 display.

## Wiring of the ILI9341:

```
ILI9341   -> ESP32
VCC       -> 3.3V
GND       -> GND
CS        -> 15
RESET     -> 
D/C       -> 2
SDI(MOSI) -> 13
MISO      -> 12
SCK       -> 14
LED       -> 21
```


## Files required

Copy the following files into your Home Assistant ESPHome folder, for example /homeassistant/config/esphome:

```
power_display.h
electrical_tower32.png
solar_energy32.png
```
Use the file power-display-esphome.yaml to create your ESPHome entity.

## Datasources and connection to Home Assistant
Data sources from Home Assistant are defined in power-display-esphome.yaml

It will require the HomeAssistant integration with NordPool (https://github.com/custom-components/nordpool), as well as a device that can read the current power usage from the power meter. 

### Popular ESPHome implementations are:

- Home Assistant Glow pulse counter. (https://klaasnicolaas.github.io/home-assistant-glow/)
- ESPHome HAN port reader  (https://github.com/psvanstrom/esphome-p1reader)

The implementation also expects a Utility Meter entity in Home Assistant. The following is an example to put in configuration.yaml:
```
 utility_meter:
 produktion_huset_per_dag:
   source: sensor.cumulative_active_export
   cycle: daily
```

## Backlight entity
PowerDisplayESPHome creates an entity in Home Assistant that can be used to control the brightness of the display, or turn it off with a schedule etc.

## Casing
STL files are available for 3D printing a casing for the display.

    
