# MipmapFix
Ever noticed that distant textures become *very* fuzzy when introducing a mod or two, maybe a resource pack? 
Here's your fix.

## Visual Comparison
The difference is not actually immediately noticeable, unless you look closely at the images.

<p align="center">Before vs After</p>

<p align="center">
<img src="/gallery/before.png" width="256">
<img src="/gallery/after.png" width="256">
</p>

## Why does this happen?
One of your mods or resource packs has a texture that isn't a power of two being used in the blocks
or items. A power of two texture is 16x16, 32x32, 64x64, 128x128, etc.

Your textures should always be a power of two regardless, even if they're being added to a texture atlas
that is already a power of two. It's nice to have a standard, and for any textures that aren't on an atlas,
they would provide [some rendering optimizations](https://gamedev.stackexchange.com/questions/26187/why-are-textures-always-square-powers-of-two-what-if-they-arent)
on their own.

## Why doesn't this happen on (Neo)Forge?
[They have their own fix for this](https://github.com/neoforged/NeoForge/blob/1.21.1/patches/net/minecraft/client/renderer/texture/SpriteContents.java.patch), which I ported
to mixin into [Kilt](https://modrinth.com/mod/kilt), then adapted into its own mod because for some reason
no one else has done this. Everyone that has is all me.
