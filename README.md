# Specification for level type C1 `v0.0.1`

### Layout
Layout for a chunk(1 char is a bit): `ERRPTTTT`<br>
E = The next chunk is a "extra chunks" (can be used to store extra data like cell types or whatever)<br>
R = Rotation<br>
P = Placeable<br>
T = Type<br>

Layout for a "extra chunk": `CCCDDDDD`<br>
C = Type of the chunk
    If its 0b00: repeat the previos cell using the D
    If its 0b01: TODO (prob some sort of compression)
    If its 0b10: TODO
    If its 0b11: use the data to extend the cell types `(((prevchunk&0b1111)<<4)|(thischunk&0b1111))`<br>
D = The data<br>

Layout for the level string: `C1;<stride>;<title|desc>;<chunks in base64 format>`
Title and description must be escaped of | and ; bcs ; is used as the seperator for the level string stuffs and | is used to sepereate the title and desc

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

(1010) Disabler
(1011) Unknown (When exporting from a remake that has more cells you can use this for cells that arent here)
(other) Perhaps
```

Example implementation: TODO
