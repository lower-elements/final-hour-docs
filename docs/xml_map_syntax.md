# The New XML Map Syntax

## Getting Started

Each map should have a `<map>` as its root element. This should have only 1 attribute (`bounds`) that specifies the minimum and maximum coordinates for the bounding box.

### Bounds

The `bounds` attribute is the most common attribute after `id` and `class` (we'll get to those later). This is because most map elements such as doors, zones, platforms, etc., are defined as 3D bounded boxes.

To define bounds, the value of the attribute should be 6 numbers separated by spaces, in the following exact order: `minX maxX minY maxY minZ maxZ`
For example:

`<map bounds="0 10 0 20 0 100"/>`

The above will make the map rectangular, spanning 10 tiles x (left to right), 20 tiles y (backwards to forward), and 100 tiles z (downwards to upwards). Note that no entity will ever be able to cross the map's bounds.

### The Head Element

The `<head>` element is used to define metadata about the map. This will be expanded in the future; however, right now, this element can have one element as its child:

#### The Public Element (Optional)

The `<public/>` element takes no attributes and no children. Thus, it is recommended to use it as a self-closing tag (`<public/>`)

When the public element exists, this map will be public (players will be able to create matches using it). If it was removed or if it wasn't defined in the head tag in the first place, this map will not be public (only builders will be able to access it).

### The `body` Element

Most of the map's content will be inside this element. The `<body>` element defines the content of the map (platforms, zones, doors, windows, etc), which shall from now on be refered to as map semantic elements or map semantics.

## Map semantic elements.

map semantic elements are what you use to define your map's shape and other characteristics. These elements can only go in the `body` element.

Before we dive into these elements,  let's clarify some keywords:

-   Attributes: These are key-value pairs that provide information about an element. They are written within the opening tag like this: `<tag attribute1="value1" attribute2="value2">`.
-   Text Content: Some elements can have text content between the opening and closing tags, like this: 

``` xml
<element>
This is the text content
</element>
```

Here's an example showing both attributes and text content:

``` xml
<tag attribute1="value1" attribute2="value2">
This is the text content
</tag>
```

### `id` and `class` attributes:

sometimes you need to give your elements some extra identity. That's where the `id` and `class` attributes come into play. Every single semantic element accepts these attributes, but they are not strictly required. Only define them when you need them:

#### `id` Attribute

The `id` attribute provides a unique identifier for an element within your map, making it easy to refer to them individually.

For example, if you have a specific platform or door that you want to reference elsewhere in your map, you can give it a unique `id`:

``` xml
<platform id="mainPlatform" bounds="0 10 0 20 0 0" type="wood"/>
```

Now, you can easily target this platform by its ID whenever you need to interact with it in your map script or otherwise.

#### `class` attribute.

On the other hand, the `class` attribute allows you to categorize elements into groups.

For example, if you have multiple platforms in your map that are made of wood, you can give them all the same class:

``` xml
<platform class="woodenPlatform" bounds="0 10 0 20 0 0" type="wood"/>
<platform class="woodenPlatform" bounds="20 30 0 20 0 0" type="wood"/>
```

Now, you can easily target all wooden platforms at once by referencing their class name.

Now, let's go through the different map semantic elements you can have:

#### area

##### Attributes:

- bounds (required): space-separated list of 6 integers. The bounds of this area, formatted as minX maxX minY maxY minZ maxZ

##### Child Elements:

The area element can contain any semantic element(s) as its children, including other areas.

##### Behavior:

All `bounds` and `position` attributes of child elements within an `area` are relative to the bounds of that area element. If an area element is nested within another area, its bounds and position attributes, as well as those of its children, are relative to the parent area. This continues recursively until the outermost area, whose bounds and position attributes are relative to the map's overall bounds.

Suppose we have an area with bounds="10 20 10 20 10 20", representing an area that starts at (10, 10, 10) and extends to (20, 20, 20) within the map's bounds.

Within this area, we have a platform with bounds="2 4 2 4 0 0". Since the platform's bounds are relative to the parent area's bounds, the actual bounds of the platform within the map would be calculated as (10 + 2, 10 + 4, 10 + 2, 10 + 4, 10 + 0, 10 + 0), which translates to (12, 14, 12, 14, 10, 10) in the map's coordinate system.

#### Platform

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this platform, formatted as `minX maxX minY maxY minZ maxZ`
-   type (required): string. The tile or wall type of this platform

#### Music

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this music zone, formatted as `minX maxX minY maxY minZ maxZ`
-   sound (required): string. The path (relative to the game's `data` folder) of the sound file to play as music

#### Ambience

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this ambience zone, formatted as `minX maxX minY maxY minZ maxZ`
-   sound (required): string. The path (relative to the game's `data` folder) of the sound file to play as ambience
-   volume (optional): number. The volume of the ambience sound

#### Sound Source

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this sound source, formatted as `minX maxX minY maxY minZ maxZ`
-   sound (required): string. The path (relative to the game's `data` folder) of the sound file to play
-   volume (optional): number. The volume of the sound

#### Pannable

##### Attributes:

-   position (required): space-separated list of 3 integers. The position of this pannable sound, formatted as `x y z`
-   sound (required): string. The path (relative to this game's `data` folder) of the sound file to play
-   volume (optional): number. The volume of the sound

#### Zone

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this zone, formatted as `minX maxX minY maxY minZ maxZ`

##### Text Content:

The text content of this element describes the text content of this zone

#### Door

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this door, formatted as `minX maxX minY maxY minZ maxZ`
-   walltype (required): string. The wall type of this door
-   tiletype (required): string. The tile type of this door
-   minpoints (required): number. The minimum number of points required to activate this door
-   activates (optional): string. The class of other elements that this door activates when opened

#### Reverb

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this reverb zone, formatted as `minX maxX minY maxY minZ maxZ`
-   decay_time (optional): number. The room decay time.seconds
-   density (optional): number. The density of the reverb effect.
-   diffusion (optional): number. The diffusion of the reverb effect.
-   gain (optional): number. The overall reverb gain.
-   gainhf (optional): number. The high-frequency reverb gain, ranging from 0.0 (no high-frequency reverb) to 1.0 (maximum high-frequency reverb)
-   gainlf (optional): number. The low-frequency reverb gain, ranging from 0.0 (no low-frequency reverb) to 1.0 (maximum low-frequency reverb)
-   hfratio (optional): number. The high-frequency to low-frequency ratio.
-   lfratio (optional): number. The low-frequency to high-frequency ratio.
-   reflections_gain (optional): number. The early reflections gain.
-   reflections_delay (optional): number. The early reflections delay time.
-   reflections_pan (optional): space-separated list of 3 numbers. The early reflections panning vector, formatted as `x y z`
-   late_reverb_gain (optional): number. The late reverb gain.
-   late_reverb_delay (optional): number. The late reverb delay time.
-   late_reverb_pan (optional): space-separated list of 3 numbers. The late reverb panning vector, formatted as `x y z`
-   echo_time (optional): number. The echo time.
-   echo_depth (optional): number. The echo depth.
-   modulation_time (optional): number. The modulation time.
-   modulation_depth (optional): number. The modulation depth.
-   air_absorption_gainhf (optional): number. The air absorption high-frequency gain, ranging from 0.0 (no high-frequency absorption) to 1.0 (maximum high-frequency absorption)
-   hfrefference (optional): number. The high-frequency reference.
-   lfrefference (optional): number. The low-frequency reference.
-   room_rolloff_factor (optional): number. The room rolloff factor.

#### Wallbuy

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this wallbuy, formatted as `minX maxX minY maxY minZ maxZ`
-   weapon_name (required): string. The name of the weapon being sold at this wallbuy
-   weapon_cost (required): number. The cost of the weapon being sold at this wallbuy
-   ammo_cost (required): number. The cost of the ammo being sold for the weapon at this wallbuy

#### PlayerSpawn

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this player spawn, formatted as `minX maxX minY maxY minZ maxZ`

#### ZombieSpawn

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this zombie spawn, formatted as `minX maxX minY maxY minZ maxZ`
-   name (optional): string. The name of the zombie type to spawn
-   z_bound (optional): boolean. Whether zombies should stop spawning through this zombie spawn if no player is in its z coordinates.

#### Interactable

##### Attributes:

-   bounds (required): space-separated list of 6 integers. The bounds of this interactable, formatted as `minX maxX minY maxY minZ maxZ`

#### PerkMachine

##### Attributes:

-   position (required): space-separated list of 3 integers. The position of this perk machine, formatted as `x y z`
-   perk (required): string. The name of the perk being sold at this machine
-   quantity (optional): number. The quantity of the perks in this machine
-   price (optional): number. The price of the perk being sold
-   allowDuplicate (optional): boolean. Whether to allow the player to purchase the perk multiple times
-   sound (optional): string. The sound of the perk machine (plays in a loop if the machine is working)

#### PowerSwitch

##### Attributes:

-   position (required): space-separated list of 3 integers. The position of this power switch, formatted as `x y z
- cost (required): number. The cost to activate this power switch.

#### window

##### Attributes:

-   position (required): space-separated list of 3 integers. The position of this window, formatted as `x y z
- health (required): number. The health of this window.