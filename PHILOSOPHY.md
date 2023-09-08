# Philosophy

## General


### #1: Cardinal Rule (Legacy Code)

It's okay to let old things die.

Every feature we keep is a feature the code for which needs to be understood, refactored, unit-tested, maintained, and tested on all supported platforms. 

Features that maintain support for specific hardware devices like old sound cards introduce more edge cases and testing configurations. We could implicitly 
trust that all that sound device code we inherit is extremely mature and works on Linux, Windows, macOS, and the BSDs, and never have an issue. But we'd also 
never see an issue because no one is ever going to be using that configuration, let alone bug reporting back to us. And I don't really want people to be using 
those configurations, because if they did have an issue, I'm not going to have the time or resources (literally the physical hardware) to do something about it.

It would be a lot of effort going into something that will have a miniscule impact.

### #2: If audio can't happen through SDL/SDL Mixer, it can't happen at all.

Follow the "do one thing and do it well" approach here. That "one thing" being getting our noises to the speaker. The hardware support for a physical OPL or PC speaker will be removed (See #1 for rationale). 
We have SDL emulations of these. 

3. We should keep the code for [digital music pack support](https://www.chocolate-doom.org/wiki/index.php/Digital_music_packs) as it would form the basis for the engine
  being able to play `.ogg` files which is pretty important. But it would be less 'digital music packs' and just 'music' usable at the game developers discretion.
4. Remove the Gravis Ultrasound emulation.
5. Use or build upon the tooling to create `GENMIDI` lumps with custom instruments for the OPL emulation. This could be a pretty cool novelty feature of a 'retro/fantasy' engine.

### MIDI playback
- In software only, inside the game only.
- Anything that requires the user to install/configure something _outside_ the game isn't the vibe.
- Can't maintain support for hardware devices / operating system MIDI support, etc.

Part of the reason I like the OPL emulation so much is that it's all portable with no dependencies, it's just in the game and in the WAD. If we can keep the same thing going with
libfluidsynth, embedded into the game (not requiring external programs) that might be an option. But then game developers will need to distribute Soundfonts, either inside the 
`WAD` as something like a `SNDFONT` or `SOUNDFNT` lump, or outside the WAD. Having all the game data inside the WAD keeps things simple for distribution. But game 
developers would need to choose Soundfonts carefully. Large soundfonts would balloon the size of the WAD.
