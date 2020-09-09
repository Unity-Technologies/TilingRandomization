# Tiling Randomization
Randomized Tiling for Unity ShaderGraph
Works with: 2019.4 LTS, 2020.1, 2020.2

Get rid of tiling artifacts in your shaders by randomizing the tiling.

![Before: Standard Tiling](/.images/TilingRandomizationBefore.jpg)

![After: Randomized Tiling](/.images/TilingRandomizationAfter.jpg)

How it's done:

Split the UV plane into three groups of hexagons, here colored red, green and blue.
![Hexes: Tiling Regions](/.images/TilingRandomizationHexes.jpg)

Each hexagon chooses a unique randomized tiling.
Here we display the random values of each hex tile.
![Random: Per-Tile Random Values](/.images/TilingRandomizationValue.jpg)

We blend the hexagons together.
Any pixel fragment only has to consider three neighboring hexagons, one from each of the three groups.

The relative cost, compared to a regular tiling texture fetch, is is a bit of math (which is largely "free" on modern GPUs) and three texture fetches, one for each of the neighboring hexagons.
