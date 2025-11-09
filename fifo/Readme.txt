#FIFO stands for First In, First Out — it’s a hardware buffer that stores data in the order it’s written and reads it out in the same order.

#FIFO WIDTH:
Width means how many bits each data item (word) in the FIFO can hold.
Example:
  -> logic [7:0] din;
means the FIFO handles 8-bit data (1 byte per entry).
So each “slot” inside the FIFO can store an 8-bit value.
If width = 8 → each entry stores 8 bits
If width = 16 → each entry stores 16 bits
If width = 32 → each entry stores 32 bits (1 word)

#FIFO Depth:
Depth means how many data entries the FIFO can store at once — i.e., how many words it can hold before becoming full.
Example:
  -> logic [7:0] mem [0:3];
Width = 8 bits
Depth = 4 entries (0,1,2,3)
So total storage = 8 bits × 4 = 32 bits.

4	-> Can store 4 data words ->	Shallow FIFO
16 ->	Can store 16 data words	-> Common in small buffers
1024	-> Can store 1024 data words -> Large FIFO for streaming

Design:
parameter int WIDTH = 8;
parameter int DEPTH = 16;
logic [WIDTH-1:0] mem [DEPTH];

FIFO (WIDTH=8, DEPTH=4)

         +-------------------------+
Write -> | [7:0] | [7:0] | [7:0] | [7:0] | -> Read
         +-------------------------+
           Slot0   Slot1   Slot2   Slot3
Each slot holds 8 bits.
There are 4 such slots = depth of 4.
