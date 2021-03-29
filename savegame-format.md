# Savegame format for settlers 1

The savegame for settlers 1 is divided into parts for common fields, players, map, settlers, flags, buildings and inventories.
**Important: The bytes are saved as little endian.**

## Main parts
- Common fields: 250 Bytes (Offset 0)
- Players 1-4: 8628 Bytes per player (1: Offset 250, 2: Offset 8878, 3: Offset 17506, 4: Offset 26134)
- Map: 8 Bytes per element; amount depends on map size (element count can be found in common fields)
- Settlers used index: 8008 Bytes for a maximum of 64.043 settlers (1 Bit = 1 settler, 1 Byte = 8 settlers)
- Settlers data: 16 bytes per settler; amount depends on last used index (index can be found in common fields)
- Flags used index: 2052 Bytes for a maximum of 16.391 flags (1 Bit = 1 flag, 1 Byte = 8 flags)
- Flags data: 70 bytes per flag; amount depends on last used index (index can be found in common fields)
- Buildings used index: 1200 Bytes for a maximum of 9.576 buildings (1 Bit = 1 building, 1 Byte = 8 buildings)
- Buildings data: 18 bytes per building; amount depends on last used index (index can be found in common fields)
- Inventories (additional object for castle and stock) used index: 184 Bytes for a maximum of 1.444 inventories (1 Bit = 1 inventory, 1 Byte = 8 inventories)
- Inventories (additional object for castle and stock) data: bytes per inventory; amount depends on last used index (index can be found in common fields)

## Common fields
- Map - Index mask: 4 Bytes (Offset 0)
- Map - Byte move direction right: 4 Bytes (Offset 4)
- Map - Byte move direction down right: 4 Bytes (Offset 8)
- Map - Byte move direction down: 4 Bytes (Offset 12)
- Map - Byte move direction left: 4 Bytes (Offset 16)
- Map - Byte move direction up left: 4 Bytes (Offset 18)
- Map - Byte move direction up: 4 Bytes (Offset 22)
- Map - Byte move direction up right: 4 Bytes (Offset 26)
- Map - Byte move direction down left: 4 Bytes (Offset 30)
- Unknown: 4 Bytes (Offset 34)
- Map - Element count: 4 Bytes (Offset 38)
- Map - Row shift: 2 Bytes (Offset 42)
- Map - Column mask: 2 Bytes (Offset 44)
- Map - Row mask: 2 Bytes (Offset 46)
- Map - Element offset for second data: 4 Bytes (Offset 48)
- Map - Column size: 2 Bytes (Offset 52)
- Map - Shift for row mask: 4 Bytes (Offset 54)
- Map - Column pairs: 2 Bytes (Offset 58)
- Map - Row pairs: 2 Bytes (Offset 60)
- Map - Columns: 2 Bytes (Offset 62)
- Map - Rows: 2 Bytes (Offset 64)
- ...
- Last used flag index: 2 Bytes (Offset 90)
- Last used building index: 2 Bytes (Offset 92)
- Last used settlers index: 2 Bytes (Offset 94)
- ...
- Last used inventory index: 2 Bytes (Offset 174)
- ...
- Map - Size: 2 Bytes (Offset 190)

## Player
- ...
- Number: 2 Bytes (Offset 128)

## Map
Elements are divided into two parts of 4 Bytes each. The difference in bytes can be found in common fields (offset to second data).

## Settler
- Type and owner: 1 Byte (Offset 0)
    - Bit 7   = Unknown (10000000)
    - Bit 2-6 = Type (01111100)
    - Bit 0-1 = Owner (00000011)
- Animation: 1 Byte (Offset 1)
- Counter: 2 Bytes (Offset 2)

## Flag

## Building

## Inventory
