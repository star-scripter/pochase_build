# 🗺️ Map Generation
Procedural generation system to create infinite scrolling in the game.

## 1. Scrolling per Chunk
#### Script: MapGenerator_2D.gd
1. Spawns 4 instances of the background chunk to fill the screen using _spawn_chunk()
2. Moves the map chunk by scroll_speed * delta in _process()
3. When chunk moves off screen, it is deleted using _despawn_chunk()
4. At the same time, a new chunk is spawned on top of the topmost screen to maintain the impression of a loop


## 2. Gridlock System (3 x 3)
#### Script: MapGenerator_2D.gd
Each chunk is subdivided into 3 rows and 3 columns. 
- The horizontal space (X-axis) is divided to 3 fixed lanes: x = -200.0, x = 0.0, x = 200.0. 
- The vertical space (Y-axis) is divided to 3 vertical slots: y = 250.0, y = 572.0, y = 894.0

### Scheme
| Lane 1 | Lane 2 | Lane 3 |
| ------ | ------ | ------ |
| A1 | B1 | C1 | 
| A2 | B2 | C2 |
| A3 | B3 | C3 | 

## 3. Difficulty Scaling
#### Script: MapGenerator_2D.gd

### 3.1. Obstacle Generation
Two types of obstacle generation:
1. Easy: 
   - Score range: 0 - 1000
   - 50% 1 obstacle per row, 50% 2 obstacle per row
   - Rule 1: No vertical stacking (no A1-A2)
   - Rule 2: Sparse patterning, diagonal placement (A1-B2, B2-C3, etc.) not allowed

2. Hard:
   - Score range: 1000>
   - 30% 1 obstacle per row, 70% 2 obstacle per row
   - Rule 1: Vertical stacking allowed, but there is always one valid path through the chunk (so the game is not impossible)
   - Rule 2: Diagonal placement is allowed, but not for tall obstacles

### 3.2. Speed Boost
- General Speed Increase: **+2 pixels/second**
- Max Speed: Capped at **800** pixels/second
- During boost: **x2** from original speed
