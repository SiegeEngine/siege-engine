# Siege Engine FAQ

Table of Contents
=================

* [Siege Engine FAQ](#siege-engine-faq)
  * [General](#general)
    * [What is the Siege Engine?](#what-is-the-siege-engine)
    * [Why are the client, server, and network component missing?](#why-are-the-client-server-and-network-component-missing)
    * [Is this a Game?](#is-this-a-game)
    * [What executable do I run?](#what-executable-do-i-run)
    * [What games are being developed using this engine?](#what-games-are-being-developed-using-this-engine)
    * [Who is behind the Siege Engine?](#who-is-behind-the-siege-engine)
    * [MMO? Really? Aren't MMOs gigantic projects?](#mmo-really-arent-mmos-gigantic-projects)
    * [What is the Goal of the Siege Engine](#what-is-the-goal-of-the-siege-engine)
    * [Why build yet another game engine?  Why not use Unreal Engine or Unity?](#why-build-yet-another-game-engine--why-not-use-unreal-engine-or-unity)
    * [How long has this been in development?](#how-long-has-this-been-in-development)
    * [Are these really the most frequently asked questions?](#are-these-really-the-most-frequently-asked-questions)
  * [Vulkan Related](#vulkan-related)
    * [What is the Vulkan API?](#what-is-the-vulkan-api)
    * [What is wrong with OpenGL?](#what-is-wrong-with-opengl)
  * [Rust Related](#rust-related)
    * [What is the Rust language?](#what-is-the-rust-language)
    * [Why not use C\+\+?](#why-not-use-c)
    * [Why not use C\#?](#why-not-use-c-1)
    * [Why does this not use the piston\-engine?](#why-does-this-not-use-the-piston-engine)
    * [Why does this not use the vulkano library?](#why-does-this-not-use-the-vulkano-library)
    * [Why does this have its own UI library and not use conrod?](#why-does-this-have-its-own-ui-library-and-not-use-conrod)
  * [Code Related](#code-related)
    * [Why does the first commit of many of these libraries contain so much code?](#why-does-the-first-commit-of-many-of-these-libraries-contain-so-much-code)
  * [Renderer Related](#renderer-related)
    * [What style renderer is used](#what-style-renderer-is-used)
    * [Why is the depth buffer backwards?](#why-is-the-depth-buffer-backwards)
    * [What rendering phases can I plug into?](#what-rendering-phases-can-i-plug-into)
    * [What render passes does siege\-render undergo?](#what-render-passes-does-siege-render-undergo)
    * [Why does the terrain plugin take so long to render](#why-does-the-terrain-plugin-take-so-long-to-render)
    * [Why is terrain heightmap based? Will there be other types of terrain? Voxels?](#why-is-terrain-heightmap-based-will-there-be-other-types-of-terrain-voxels)
    * [Where are the character models and animations?](#where-are-the-character-models-and-animations)
  * [Asset pipeline related](#asset-pipeline-related)
    * [Why is the mesh format custom? Why not use assimp?](#why-is-the-mesh-format-custom-why-not-use-assimp)
  * [Network Related](#network-related)
    * [Why is siege\-net on top of UDP?](#why-is-siege-net-on-top-of-udp)
    * [What network security is being used?](#what-network-security-is-being-used)
  * [Appendix](#appendix)
    * [My question was not addressed](#my-question-was-not-addressed)

## General

### What is the Siege Engine?

The Siege Engine is an MMO Game Engine targetting the Vulkan API and written in the
Rust language.

### Why are the client, server, and network component missing?

This is temporary. We are in the process of removing game-specific
proprietary code. Once that is complete to our satisfaction, these
major components will be released.

### Is this a Game?

No, it is only a set of libraries useful for buildling a game.

### What executable do I run?

There is none. If you are not a developer, you will find the siege engine is of
little use to you.

### What games are being developed using this engine?

Only one so far that I know of: The Eye of Ba'al. That game is far from complete,
please do not anticipate it.  The developer of that game decided to open-source
the engine component, while keeping the game-specific components proprietary.
The Siege Engine is that open-sourced component.

We hope the engine can become useful enough for additional games to use it.

### Who is behind the Siege Engine?

[Michael Dilger](https://github.com/mikedilger) from New Zealand (and formerly of
California) is the founder and lead developer. [Gnomonic Games](http://gnomonicgames.com)
is his game venture. [Optimal Computing](https://optcomp.nz) is his consulting
company.

Other developers are encouraged to contribute.

### MMO? Really? Aren't MMOs gigantic projects?

Yes. MMOs are gigantic projects. The engine is just one part of an MMO. MMOs
also require very advanced server technologies, game rulesets, and of course
a virtual world with plenty of art, animations, etc, not to mention the business
and management of the customer relationships, investors, media, etc.

The Siege Engine is only an engine, and primarily the client-side of an engine.
Further, it is not a complete game, but requires additional game-specific code
in order to flesh out an actual game.

While it is still a big project, it is nowhere near the scale of an MMO project.

The reason we call it an MMO engine (the first M standing for Massively) is that
we see no reason that the engine could not support massive player-bases (eventually),
and see no reason to limit ourselves.

### What is the Goal of the Siege Engine

The longterm goal is to provide a fully open-sourced and community driven MMO client
and protocol, enabling multiple "game world" providers to run potentially commercial
services that are compliant with the client/protocol. With enough standardization,
alternate compatible clients could be developed in the future.

It remains to be seen how much can be standardized and how much is game specific, and
where exactly to draw the line. This project started to support a specific game, but
is transitioning towards being as game-agnostic as possible.

While being game-agnostic, specific modules/plugins/libraries supporting traditional
classic MMO feature sets will be developed and open-sourced, alleviating the heavy-
lifting required to build a new game.

### Why build yet another game engine?  Why not use Unreal Engine or Unity?

Those engines rely on languages that we do not prefer.
Further, they require commercial licensing.

In truth, the developer is not intimately familiar with every game engine
that is out there (and there are scores). But it is already clear, looking out
from the rust community, that none of them are written in rust, except piston,
and we have a FAQ question about that below.

### How long has this been in development?

In its current form, since about May 2017. A previous version on vulkano was
started in early 2017. Prior to that, another engine ("vast") using rust/OpenGL
was developed between 2014 and 2017. Work before that used C++ and extends
back to 2009 and used Ogre3D and RakNet. Some of that early work remains to be
reimplemented.

### Are these really the most frequently asked questions?

No. I have collected no statistics. This is just a convenient format to
disseminate information.

## Vulkan Related

### What is the Vulkan API?

Vulkan is a new generation graphics and compute API that provides high-efficiency,
cross-platform access to modern GPUs used in a wide variety of devices from PCs
and consoles to mobile phones and embedded platforms.
See [Vulkan](https://www.khronos.org/vulkan).

If you want both cross-platform and high-performance, Vulkan is the answer.

Vulkan was created by the same organisation that created OpenGL, the Khronos group.

### What is wrong with OpenGL?

Nothing is wrong with OpenGL. OpenGL is not going away and is the right solution
where the highest performance is not required. The Siege Engine intends to support
games of high commercial quality, and these types of games require the highest
performance API available.

## Rust Related

### What is the Rust language?

[Rust](https://rust-lang.org) is a systems programming language that runs blazingly fast,
prevents segfaults,
and guarantees thread safety. Performance is on-par with C++, but safety and ergonomics
are much better. No segfaults, no bad pointers, no double frees, no memory leaks,
zero-cost high level abstractions, thread safety, very convenient packaging, ergonomic
module layout, and more. And you get minimal runtime binaries that run at system speeds
very similar to what you would get out of C or C++.

The downside of rust is lifetime management. While this is somewhat difficult for
beginners, experienced rust developers rarely have difficulties managing them.

Rust is developed by the Mozilla Organisation,
the same people who brought us the Firefox web browser.

### Why not use C++?

We think that the rust language simply offers a better deal.

C++ is common in game engine development, however. Epic Games' Unreal Engine, for
example, is written in C++. By moving to rust, however, we do not need to leave all that
legacy code behind. Rust programs can link to C++ programs with extern "C" functions.

### Why not use C#?

C# has another set of language issues I could get into, much of which it shares
with Java. But an even bigger issue is that C# is strongly tied into .NET and the
Microsoft Windows family of operating systems, making it "vendor locked."

C# is used by the popular Unity engine, however Unity itself is cross-platform.

### Why does this not use the piston-engine?

We actually do use some libraries from the piston engine such as `image` and
`ddsfile`. However, not the core engine itself, as we find that we are targeting
different purposes.

We are excited about dyon and hope to investigate it further.

### Why does this not use the vulkano library?

Most rust FFI libraries ship with two crates: a system level crate, and a higher
level crate providing Rust-style abstractions. Vulkano follows that pattern.

But vulkan is a very complex and fragile API. In order to guarantee safety,
the high level crate must do an incredible amount of work.

We used vulkano early on, but moved away from it as we found numerous cases
where vulkano was not yet ready, and open issues remaining stagnant.

Another crate `dacite` took a different approach. It handled/wrapped the low-level
unsafes, and handled memory management with wrapping types, and did not do much
else. In this way, the full Vulkan API is exposed and is thread-safe and memory-safe,
but doesn't go so far to ensure you meet all the requirements of the Vulkan API.
Using this tack, dacite was complete and stable much sooner than vulkano.

We instead use the Vulkan validation layers (and frequent reads of the Vulkan
specification) to help ensure that we are using the Vulkan API correctly.

### Why does this have its own UI library and not use conrod?

The siege-engine UI library is very new and was developed to get something on the
screen quickly, without much regard to other libraries available. It is now about
time to look around for something more than the fledgling UI we currently have,
and conrod is on our radar.

However, [this issue](https://github.com/PistonDevelopers/conrod/issues/1103) leads
us to believe conrod (connie?) has made specific choices which do not align with
our goals, and thus may not be usable by the siege engine. Even if that turns out
to be the case, we hope to learn as much as we can from it.

## Code Related

### Why does the first commit of many of these libraries contain so much code?

The actual history of these libraries has been elided because it contained
game-specific proprietary code. The first commit represents the state of the
library after the game-specific proprietary code was removed.

Several libraries retain their full history: `siege-math`, `siege-color`, and
`ddsfile`, possibly more (this FAQ may not be up to date).

## Renderer Related

### What style renderer is used

`siege-render` uses a deferred shading style renderer. We started out doing
forward rendering with an early depth pass, but found it too difficult to unify
the shading across all of the different components.

We provide a *transparent* pass, wherein the library consumer may shade in any
which way they wish.

### Why is the depth buffer backwards?

[This page](https://developer.nvidia.com/content/depth-precision-visualized)
says it best.

### What rendering phases can I plug into?

Right now, `geometry`, `transparent`, and `ui`, although the siege-engine is
undergoing constant development, and I expect the renderer to change many
more times yet before it settles down.

### What render passes does siege-render undergo?

There are currently six logical passes, but I expect more because we do not
yet handle volume rendering, shadows, rayleigh scattering, etc. Under Vulkan,
the incremental cost of another renderpass is negligable.

* **Geometry**: This is where you draw your geometry. Your shaders need to
  output data to the g-buffers, which includes diffuse, normals and material
  information.
* **Shading**: This internal pass is where enhanced physically based Blinn-Phong
  shading occurs, based on the g-buffer data.
* **Transparent**: This is the opportunity to render transparent objects, or indeed
  any rendering that you don't want to be shaded by the shading pass, other
  than UI.
* **Blur**: This internal pass (actually two passes) handles blur and bloom effects.
* **Post**: This internal pass handles post processing including tonemapping and
  sRGB adjustments (where necessary).
* **UI**: This is where you render your UI components, on top of everything else.
  The depth buffer is cleared and again available at this point.

### Why does the terrain plugin take so long to render

The terrain plugin is fledgling, and we are not doing LOD at all yet. Also, it
currently uses five texture maps (albedo, normal, ambient occlusion, roughness,
and cavity) and texture lookups have a definite cost.

### Why is terrain heightmap based? Will there be other types of terrain? Voxels?

The terrain plugin is a plugin precisely because this level of detail is not
something we can dictate. You are not tied into this particular way of handling
terrain. You may not even be an outdoorsy style game. Each game has it's own
requirements.

We provide a heightmap based terrain presently because that was fairly easy for
us to achieve quickly. Feel free to develop a better one.

### Where are the character models and animations?

Art, models and animations are very game specific stuff. We will probably provide
some placeholder art to help along other parts of development, but it is not the
goal of this engine to provide any substantial game content.

That being said, having technology for dealing with character models and animations
is definately our intent. We just haven't quite gotten there yet. The piston engine
project has a skeletal animation library we need to look into.

## Asset pipeline related

### Why is the mesh format custom? Why not use assimp?

This is an area that needs a lot of development still. The custom format is a
placeholder until that more thoughtful development takes place.

## Network Related

### Why is siege-net on top of UDP?

UDP is the only widely available Internet wide protocol that could world well for us.
TCP has issues around the Nagle algorithm, and retransmits and reassemblies that
are forced upon us even in cases when we don't want them. SCTP and similar are
not reliably available Internet-wide.

We didn't have to build on top of UDP from scratch, we could have used another
layer that handled the retransmission, multiplexing, flow and congestion control.
But we have not yet found such a library that we really like, so we are staying
put for the moment. This could easily change.

### What network security is being used?

In short, A secure session is established using ephemeral keys and X25519 key agreement.
Clients authenticate the server via a well known public key signing a client-supplied
nonce.  Packets are signed and authenticated (AEAD) using AES_128 GCM, which is
implemented in hardware on x86_64 platforms, so it goes really fast. The author
used to work as a Computer Security researcher and isn't a stranger to cryptography,
nor to its insidiously difficult-to-get-right nature. Nonetheless, we probably did
it wrong. ;-)

## Appendix

### My question was not addressed

Please, open an [issue](https://github.com/SiegeEngine/siege-engine/issues)
