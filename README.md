# Specification for level type C1 `v0.0.1`

### Layout
Layout for the level string: `C1;<title|desc>;<width>;<height>;<chunks in base64 format>`<br>
Title and description must be escaped of | and ; bcs ; is used as the seperator for the level string stuffs and | is used to sepereate the title and desc

Layout for a chunk/cell: `ERRPTTTT`<br>
```
E = The next chunk is a "extra chunks" (can be used to store extra data like cell types or whatever). If its not set then just add the cell to the grid
R = Rotation
P = Placeable
T = Type
```
Layout for a "extra chunk": `CCCDDDDD`<br>
```
C = Type of the chunk
    c = CCC&0b11
    if CCC&0b100 is set:
        if c is 0b00: use the data to extend the cell types `(((prevchunk&0b1111)<<4)|(thischunk&0b1111))`
        TODO
    else:
        TODO (prob some compression things)
D = The data
```
---
###  Supported cell types
```
[] means the default cells
() means special things

[0000] Empty
[0001] Generator
[0010] Mover
[0011] CW
[0100] CCW
[0101] Slide
[0110] Push
[0111] Wall
[1000] Enemy
[1001] Trash

(1010) Disabler (indev)
(1011) Unknown (When exporting from a remake that has more cells you can use this for cells that arent saveable)
(other) Perhaps
```
---
### Implementations
Example: TODO
