# ⛹️ Character Setup

## 1. General Movement
#### Script: character_body_2d.gd
- The main character is allowed to move sideways dan jump using swipe.
  - Swipe mechanism done by calculating the mouse distance between the start position and the end position. 
  - If delta position.x < 0, move player to the left, else if delta position.x > 0, move player to the right.
  -  The player moves (slides) between three fixed lanes: x = [-220, 0, 220].
  -  The player jumps using a sine-wave calculation (sin(progress * PI) * jump_height) to make sure the jump is smooth.

## 2. Obstacle Hit
#### Script: character_body_2d.gd
- The main character and obstacles has its own hitboxes. When their hitboxes collide, the system would register it as a 'hit'.
- But the game has an invincibility system, with three different types:
  1. `invincible_damage` to make temporary buffer after hitting an obstacle
  2. `invincible_power` to make invincibility active while power-up is active (discussed in game_systems.md)
  3. `invincibility timer` to make temporary buffer after power-up runs out
- When the player is invincible, only shake camera, without losing health
- When the player is **not** invincible, the player loses one health

## 3. Death
#### Script: character_body_2d.gd
- Each player is given a chance of 5 health points. When the health point reaches 0, essentially the player dies, triggering the function `die()`.
  1. Stops the game and the map scrolling
  2. Plays death sound and stops music
  3. Shakes the camera
  4. Tweens the character falling down and rotate the character 90°
  5. Bring the satpam to play the arrest animation
  6. Show game over UI

[< Back to main](main.md)
