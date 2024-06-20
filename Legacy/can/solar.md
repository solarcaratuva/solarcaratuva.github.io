---
nav_order: 3
parent: CAN
grand_parent: Legacy
has_children: false
---

## Solar (Node ID #4)

### SolarCurrent (Message ID #4)

| Field         | Type    | Bits | Range | Units |
| ------------- | ------- | ---- | ----- | ----- |
| total_current | int16_t | 0-15 |       |       |

### SolarVoltage (Message ID #5)

| Field          | Type    | Bits  | Range | Units |
| -------------- | ------- | ----- | ----- | ----- |
| panel1_voltage | int16_t | 0-15  |       |       |
| panel2_voltage | int16_t | 16-31 |       |       |
| panel3_voltage | int16_t | 32-63 |       |       |
| panel4_voltage | int16_t | 64-79 |       |       |

### SolarTemp (Message ID #6)

| Field       | Type    | Bits  | Range | Units |
| ----------- | ------- | ----- | ----- | ----- |
| panel1_temp | int16_t | 0-15  |       |       |
| panel2_temp | int16_t | 16-31 |       |       |
| panel3_temp | int16_t | 32-63 |       |       |
| panel4_temp | int16_t | 64-79 |       |       |

### SolarPhoto (Message ID #7)

| Field        | Type    | Bits  | Range | Units |
| ------------ | ------- | ----- | ----- | ----- |
| panel1_photo | int16_t | 0-15  |       |       |
| panel2_photo | int16_t | 16-31 |       |       |
| panel3_photo | int16_t | 32-63 |       |       |
| panel4_photo | int16_t | 64-79 |       |       |

