---
nav_order: 3
parent: CAN
grand_parent: Legacy
has_children: false
---

## ECU (Node ID #1)

### ECUMotorCommands (Message ID #1)

| Field                | Data Type | Bits  | Units | Cycle Time |
| -------------------- | --------- | ----- | ----- | ---------- |
| throttle             | uint16_t  | 0-15  |       | 5ms        |
| regen                | uint16_t  | 16-31 |       |            |
| forward_en           | bool      | 32    |       |            |
| reverse_en           | bool      | 33    |       |            |
| cruise_control_en    | bool      | 34    |       |            |
| cruise_control_speed | uint8_t   | 35-43 |       |            |
| motor_on             | bool      | 44    |       |            |

### ECUPowerAuxCommands (Message ID #2)

| Field             | Data Type | Bits | Units | Cycle Time |
| ----------------- | --------- | ---- | ----- | ---------- |
| hazards           | bool      | 0    | n/a   | 50ms       |
| brake_lights      | bool      | 1    | n/a   |            |
| headlights        | bool      | 2    | n/a   |            |
| horn              | bool      | 3    | n/a   |            |
| left_turn_signal  | bool      | 4    | n/a   |            |
| right_turn_signal | bool      | 5    | n/a   |            |
| ignition          | bool      | 6    | n/a   |            |
| battery_contact   | bool      | 7    | n/a   |            |
