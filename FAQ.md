# Siege Engine FAQ

Table of Contents
=================

* [Siege Engine FAQ](#siege-engine-faq)
* [Table of Contents](#table-of-contents)
  * [General](#general)
    * [What is the Siege Engine?](#what-is-the-siege-engine)
    * [Why are the client, server, and network component missing?](#why-are-the-client-server-and-network-component-missing)
    * [Is this a Game?](#is-this-a-game)
    * [What executable do I run?](#what-executable-do-i-run)
    * [What games are being developed using this engine?](#what-games-are-being-developed-using-this-engine)
    * [Is it usable now, or does it still need more development?](#is-it-usable-now-or-does-it-still-need-more-development)
    * [Who is behind the Siege Engine?](#who-is-behind-the-siege-engine)
    * [MMO? Really? Aren't MMOs gigantic projects?](#mmo-really-arent-mmos-gigantic-projects)
    * [What is the Goal of the Siege Engine](#what-is-the-goal-of-the-siege-engine)
    * [How long has this been in development?](#how-long-has-this-been-in-development)
    * [Are these really the most frequently asked questions?](#are-these-really-the-most-frequently-asked-questions)
  * [Other Engines](#other-engines)
    * [Why build yet another game engine?  Why not use an existing engine?](#why-build-yet-another-game-engine--why-not-use-an-existing-engine)
    * [How does this compare to other game engines?](#how-does-this-compare-to-other-game-engines)
    * [How does this compare to Unreal Engine?](#how-does-this-compare-to-unreal-engine)
    * [How does this compare to Unity Engine?](#how-does-this-compare-to-unity-engine)
    * [How does this compare to Godot?](#how-does-this-compare-to-godot)
    * [How does this compare to Urho3D?](#how-does-this-compare-to-urho3d)
  * [Platform](#platform)
    * [What platforms does the Siege Engine target?](#what-platforms-does-the-siege-engine-target)
    * [What about consoles?](#what-about-consoles)
    * [Does it support VR?](#does-it-support-vr)
    * [Does it support High Dyanmic Range?](#does-it-support-high-dyanmic-range)
  * [Vulkan](#vulkan)
    * [What is the Vulkan API?](#what-is-the-vulkan-api)
    * [What is wrong with OpenGL?](#what-is-wrong-with-opengl)
  * [Rust](#rust)
    * [What is the Rust language?](#what-is-the-rust-language)
    * [Why not use C\+\+?](#why-not-use-c)
    * [Why not use C\#?](#why-not-use-c-1)
    * [Why does this not use the piston\-engine?](#why-does-this-not-use-the-piston-engine)
    * [Why does this not use the vulkano library?](#why-does-this-not-use-the-vulkano-library)
    * [Why does this have its own UI library and not use conrod?](#why-does-this-have-its-own-ui-library-and-not-use-conrod)
  * [Code](#code)
    * [Why does the first commit of many of these libraries contain so much code?](#why-does-the-first-commit-of-many-of-these-libraries-contain-so-much-code)
  * [Renderer](#renderer)
    * [What style renderer is used](#what-style-renderer-is-used)
    * [Why is the depth buffer backwards?](#why-is-the-depth-buffer-backwards)
    * [What rendering phases can I plug into?](#what-rendering-phases-can-i-plug-into)
    * [What render passes does siege\-render undergo?](#what-render-passes-does-siege-render-undergo)
    * [Why does the terrain plugin take so long to render](#why-does-the-terrain-plugin-take-so-long-to-render)
    * [Why is terrain heightmap based? Will there be other types of terrain? Voxels?](#why-is-terrain-heightmap-based-will-there-be-other-types-of-terrain-voxels)
    * [Where are the character models and animations?](#where-are-the-character-models-and-animations)
  * [Asset pipeline](#asset-pipeline)
    * [Why is the mesh format custom? Why not use assimp?](#why-is-the-mesh-format-custom-why-not-use-assimp)
  * [Network](#network)
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

We hope the engine can become useful enough for additional games to use it, and
that we can find collaborators to help us develop it.

### Is it usable now, or does it still need more development?

It is certainly usable right now, *and* it also needs more development.

You could in theory write an exciting multiplayer game on the siege engine today
without any additional modifications to the engine. But it is unlikely. You
will probably find that you'll need to make changes to the engine to support your
use case.

### Who is behind the Siege Engine?

[Michael Dilger](https://github.com/mikedilger) from New Zealand (and formerly of
California) is the founder and lead developer. [Gnomonic Games](http://gnomonicgames.com)
is his game venture. [Optimal Computing](https://optcomp.nz) is his consulting
company.

Other developers are encouraged to contribute.

### MMO? Really? Aren't MMOs gigantic projects?

Yes. MMOs are gigantic projects. The engine is just one part of an MMO. MMOs
also require advanced server technologies, game rulesets, and of course
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

The primary goal is to provide a fully open-source rust-based game engine for
MMO style games.

An additional speculative longterm goal is to provide a fully open-sourced and
community driven MMO client and protocol, enabling multiple "game world" providers
to run potentially commercial services that are compliant with the client/protocol.
With enough standardization, alternate compatible clients could be developed in the
future, leaving behind a legacy of an open standard for core elements of MMO
games and their protocols.

It remains to be seen how much can be standardized and how much is game specific, and
where exactly to draw the line. This project started to support a specific game, but
is transitioning towards being as game-agnostic as possible.

### How long has this been in development?

In its current form, since about May 2017. A previous version on vulkano was
started in early 2017. Prior to that, another engine ("vast") using rust/OpenGL
was developed between 2014 and 2017. Work before that used C++ and extends
back to 2009 and used Ogre3D and RakNet. Some of that early work remains to be
reimplemented.

### Are these really the most frequently asked questions?

No. I have collected no statistics. This is just a convenient format to
disseminate information.

## Other Engines

### Why build yet another game engine?  Why not use an existing engine?

The main reason is the emergence of the Rust language. Nobody expected rust. But now that
we have it we wish to leverage it.

Existing game engines such as Unreal, Unity, CryEngine, and Godot are unlikely to
go away any time soon, and we aren't trying to replace them. Rather, we yearn for an
option in pure rust because we know that such code will be more reliable.

In truth, the developer is not intimately familiar with every game engine that is out
there (and there are scores). But it is already clear, looking out from the rust community
that none of them are written in rust, except piston, and we have a FAQ question about
that below: [Why does this not use the piston\-engine?](#why-does-this-not-use-the-piston-engine)

Lastly, it is educational and inspiring to successfully implement features of a game
engine.

### How does this compare to other game engines?

* **free and open source**: We are MIT licensed. Several other engines like Godot are also
MIT licensed, but most are commercially licensed and controlled.

* **rust based**: We are based on the rust language, whereas most other engines are based
on C++.

* **programming required**: Many leading game engines allow game developers to write games
without doing much actual programming.  You can choose options from pulldowns, drag and drop,
adjust sliders, etc, and get a game out of it. For us, this is a non-goal.

* **no editor**: While we may eventually develop an editor, it is not currently a goal.
We expect you can edit your assets/world in other tools and import them.

* **fledgling**: At least for now, we are fledgling compared to other engines.

* **libraries not framework**: Siege Engine is a collection of libraries. You may use as
many or as few as you like. Your `main()` function is yours - you own the top level
code. Some other engines own the top level.

* **limited cross-platform**: We support Microsoft Windows and Linux. We expect to be able
to support MacOS (if Vulkan becomes available there) and Android. We are unlikely to support
consoles, but never say never.

### How does this compare to Unreal Engine?

First see [How does this compare to other game engines?](#how-does-this-compare-to-other-game-engines)
for most of the answer.

Unreal is a commercially licensed engine written in C++, with extensive editing capabilities.

Unreal development started in 1998, so they are far ahead of us, but perhaps also have a
lot of baggage.

Unreal has historically had a bad reputation in the MMO space because of bugs/hacks that
are a result of their internal design, which was originally built for LAN-based games, not
Internet wide games.  Wall hacks, speed hacks, lag switches, and other hacks have caused
untold damage to numerous indie MMO companies attempting to launch games written with the
Unreal Engine.  I do not know the current state of these issues, however, but I lost trust
in this engine long ago.

Unreal Engine is the undisputed leader when it comes to photorealistic humans.

### How does this compare to Unity Engine?

First see [How does this compare to other game engines?](#how-does-this-compare-to-other-game-engines)
for most of the answer.

Unity is a commercially licensed engine written in C++, with extensive editing capabilities
and wide cross-platform support (targets 27 platform), however the engine itself must be run
on Microsoft Windows or MacOS (even though the output can target other platforms).

### How does this compare to Godot?

First see [How does this compare to other game engines?](#how-does-this-compare-to-other-game-engines)
for most of the answer.

Godot is a free and open-source MIT licensed game engine in C++. Research is ongoing.

### How does this compare to Urho3D?

Urho3D is a free and open-source game engine in C++. Research is ongoing.

## Platform

### What platforms does the Siege Engine target?

The siege engine currently targets the Linux and Microsoft Windows platforms.
However, the policy has been to be as inclusive as possible.

As rust and vulkan target more platforms, we find it easier to support them as well.
Android might already be supported (we simply haven't tried yet). MacOS would be
supported if they supported Vulkan, and there are rumored ways to make that happen
with 3rd party packages.

### What about consoles?

Consoles have very custom processors, languages, and development kits and do not
support open standards like Vulkan (yet), and are thus not supported by the Siege
Engine.

### Does it support VR?

There is no VR specific code yet, but as Vulkan supports VR it is certainly
within the realm of possibility.

VR requires rendering to two different swapchain render targets, one for each eye.
Better support for this was released in Vulkan 1.1.  Unfortunately, we can't use
Vulkan 1.1 quite yet, but this is unlikely to be a longterm issue.

### Does it support High Dyanmic Range?

Theoretically, yes.

But at least on linux, your window management system probably does not yet
understand that it should not send (255,255,255) as white (that is a *very* bright
white on an HDR monitor). The real issue in the linux world is that the linux
ecosystem is not ready for HDR.

## Vulkan

### What is the Vulkan API?

Vulkan is a new generation graphics and compute API that provides high-efficiency,
cross-platform access to modern GPUs used in a wide variety of devices from PCs
and consoles to mobile phones and embedded platforms.
See [Vulkan](https://www.khronos.org/vulkan).

If you want vendor neutral cross-platform support and also require high-performance,
Vulkan is the answer.

Vulkan was created by the same organisation that created OpenGL, the Khronos group.

### What is wrong with OpenGL?

Nothing is wrong with OpenGL. OpenGL is not going away and is the right solution
where the highest performance is not required. The Siege Engine intends to support
games of high commercial quality, and these types of games require the highest
performance API available.

## Rust

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

We think that the rust language simply offers a better deal: see
[What is the Rust language?](#what-is-the-rust-language).

C++ is common in game engine development, however. Epic Games' Unreal Engine, for
example, is written in C++. By moving to rust, however, we do not need to leave all that
legacy code behind. Rust programs can link via to any program that honors the C ABI
(as defined by the operating system), including to C++ libraries with that expose
extern "C" functions.

### Why not use C#?

C# has another set of language issues I could get into, much of which it shares
with Java. But an even bigger issue is that C# is strongly tied into .NET and the
Microsoft Windows family of operating systems, making it "vendor locked."

C# is used by the popular Unity engine, however Unity itself is cross-platform.

### Why does this not use the piston-engine?

We actually do use some libraries from the piston engine such as `image` and
`ddsfile` (which we contributed). However, not the core engine itself, as we find
that we seem to be targeting different types of games.

We are excited about [dyon](https://github.com/PistonDevelopers/dyon) and plan to
investigate it further.

### Why does this not use the vulkano library?

Most rust FFI libraries ship with two crates: a system level crate, and a higher
level crate wrapping the unsafes and providing Rust friendly types and abstractions.
Vulkano follows that pattern.

But the Vulkan API is a very complex and fragile API. In order to guarantee safety,
the high level crate must do an incredible amount of work. This makes vulkano an
extremely ambitious project.

We used vulkano early on, but moved away from it as we found numerous cases
where vulkano was not yet ready, and open issues remaining stagnant.

Another crate `dacite` took a different approach. It wrapped the low-level
unsafes, and handled memory management with wrapping types, and did not do much
else. In this way, the full Vulkan API is exposed and is thread-safe and memory-safe
and has no memory leaks or resource leaks, yet it doesn't go so far to ensure that
you cannot possibly break the requirements of the Vulkan API. Taking this tack,
dacite was complete and stable much sooner than vulkano.

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

## Code

### Why does the first commit of many of these libraries contain so much code?

The actual history of some of these libraries has been elided because it contained
game-specific proprietary code. The first commit (or series of commits) represents
the state of the library after the game-specific proprietary code was removed.

Some of the libraries retain their full history.

## Renderer

### What style renderer is used

`siege-render` uses a deferred shading style renderer. We started out doing
forward rendering with an early depth pass, but found it too cumbersome to maintain
separate shader code for each plugin.

We provide a *transparent* pass, wherein the library consumer may shade in any
which way they wish.

### Why is the depth buffer backwards?

The depth buffer 'direction' is configurable, but defaults to 'reversed'.
[This page](https://developer.nvidia.com/content/depth-precision-visualized)
explains it best.

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
  The depth buffer is cleared and again available during this pass.

### Why does the terrain plugin take so long to render

The terrain plugin is fledgling, and we are not doing LOD at all yet. Also, it
currently uses five texture maps (albedo, normal, ambient occlusion, roughness,
and cavity) and texture lookups are relatively expensive.

### Why is terrain heightmap based? Will there be other types of terrain? Voxels?

The terrain plugin is a plugin precisely because this level of detail is not
something we can dictate. You are not tied into this particular way of handling
terrain. You may not even be an outdoorsy style game. Each game has it's own
requirements.

We provide a heightmap based terrain presently because that was fairly easy for
us to achieve quickly, and it will be used in a particular game. Feel free to
develop different ones.

### Where are the character models and animations?

Art, models and animations are very game specific things. We will probably provide
some placeholder art to help along other parts of development, but it is not the
goal of this engine to provide any substantial game content.

That being said, having technology for dealing with animations is definately our
intent. We just haven't quite gotten there yet. The piston engine project has a
skeletal animation library we need to look into.

## Asset pipeline

### Why is the mesh format custom? Why not use assimp?

This is an area that needs a lot of development still. The custom format is a
placeholder until that more thoughtful development takes place.

## Network

### Why is siege-net on top of UDP?

UDP is the only widely available Internet wide protocol that could world well for us.
TCP has issues around the Nagle algorithm (corking delay), and re-transmits and
re-assemblies that are forced upon us even in cases when we don't want them.
SCTP and similar are better but not reliably available Internet-wide.

We didn't have to build on top of UDP from scratch, we could have used another
layer that handled the retransmission, multiplexing, flow and congestion control.
But we have not yet found such a library that we really like, so we are staying
put for the moment.

This state of affairs could easily change.

### What network security is being used?

In short, a secure session is established using ephemeral keys and X25519 key agreement.
Clients authenticate the server via a well known public key signing a client-supplied
nonce. Packets are signed and authenticated (AEAD) using AES_128 GCM, which is
implemented in hardware on x86_64 platforms, so it goes really fast.

The author used to work as a Computer Security researcher and isn't a stranger to
cryptography, nor to its insidiously difficult-to-get-right nature. We hope we got it
right, but there is a good chance we messed something up. We invite review and
criticism.

## Appendix

### My question was not addressed

Please, open an [issue](https://github.com/SiegeEngine/siege-engine/issues)
