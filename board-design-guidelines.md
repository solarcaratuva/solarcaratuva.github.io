# PCB Layout Guidelines
This section contains useful guidelines to generally pay attention to when laying out PCBs.

* Positive ends of ceramic bypass capacitors should be as close as possible to the pin they bypass.
  * The positive end is more important to focus on, as the GND side can easily connect to a via to the GND plane.
  * Tantalum capacitors (the polarized ones) can be kept farther away from the pins, however.
  * For example, ceramic bypass capacitors used for each VDD pin on an MCU should not be lined up next to each other on one side of the MCU and should instead be placed as close as possible to its corresponding VDD pin.

* All power lines (12V, 5V, and 3.3V) should be at least 30 mils.

* Avoid acute angles when routing.

* LSE and HSE clocks should have corresponding bypass capacitors.

* Board reset buttons should be located near the corner of the board if possible to allow for easier access. The bypass capacitor for the corresponding NRST line should be next to the MCU pin. This becomes more important the farther the reset button is from the MCU pin.

* Avoid daisy chaining GND using long traces, and instead make many short traces to vias connected to the GND plane.
  * Closer vias to the GND plane are always better than farther away ones.
  * In KiCad, when finished modifying this, make sure to refill the GND plane by right-clicking the plane and selecting `Zones > Fill All` (or use the shortcut, B).
