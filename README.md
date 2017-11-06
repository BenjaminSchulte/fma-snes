SNES library
============

This library is a basic library for the FMA assembler.


Warning
-------

This project is still in the very, very alpha version! Core features might change
without any backwards compatibility.


Example
-------

This is a simple code for initializing the ROM in HIROM

```ruby
require "engine"
require "engine/header/snes"

Debug.enable

def main
  SNES.initialize

  Debug.log "Hello world!"

loop:
  BRA loop
end

SNES.configure do

  game_code "GAME"
  game_title "My first game"
  destination :germany

  map_mode $31
  rom_type ram: true, battery: true

  memory_map do

    header_location $C0, $FFB0

    banks $C0..$FF, address: $0000..$FFFF, located_at: $0
    banks $00..$07, address: $8000..$FFFF, shadows_banks_from: $C0, shadows_addresses_from: $8000

  end

end
```


License
-------

FMA is licensed with the [MIT](./LICENSE.md) license. Author: Benjamin Schulte
