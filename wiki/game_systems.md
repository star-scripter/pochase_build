# 👾 Game Systems

## 1. Satpam Chase
#### Script: dikejar_satpam.gd

### 1.1. Chase Logic
The satpam has two states of chasing managed by the `ngejar` variable:
- `ngejar = true` then the satpam becomes close to the player. `ngejar = true` is triggered when player hits an obstacle or the game ends (player dies.)
- `ngejar = false` then the satpam retreats off the map. `ngejar = false` happens when after 5 seconds, the player doesn't hit an obstacle, or if the player uses a power up.

### 1.2. Chase Movement
The satpam moves in both the x-axis and y-axis.
- x-axis controlled by `target_lane_x` variable which follows the lane of the player (added with a time delay to make movement more realistic).
- y-axis lerps between close and far positions according to the `ngejar` variable.


## 2. Power-up System
#### Script: game_manager.gd
- The game also has a power-up system. For every 180 points, the player receives one energy bar. 
- When the player presses right click, it activates a power-up system, to which it consumes one bar.
- Effects:
  1. Speeds up the map, earns more points
  2. Makes the player invincible
  3. Forces the satpam to move back/retreat
- Visuals: Player turns gold color and semitransparent, and blinks when the power is running out.

[< Back to main](main.md)