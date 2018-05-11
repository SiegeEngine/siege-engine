# Siege Engine FAQ

* [Siege Engine FAQ](#siege-engine-faq)
  * [General](#general)
    * [What is the Siege Engine?](#what-is-the-siege-engine)
    * [Why are the client and server missing?](#why-are-the-client-and-server-missing)
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
    * [Why not use C\+\+ or C\#?](#why-not-use-c-or-c)
    * [How is this different from other rust\-based game engines?](#how-is-this-different-from-other-rust-based-game-engines)
    * [What graphics library is this based on, and why?](#what-graphics-library-is-this-based-on-and-why)
    * [Why not use cgmath or nalgebra?  Why create yet another math crate?](#why-not-use-cgmath-or-nalgebra--why-create-yet-another-math-crate)
    * [Why does this have its own UI library and not use an existing one?](#why-does-this-have-its-own-ui-library-and-not-use-an-existing-one)
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

### Why are the client and server missing?

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
please do not anticipate it.  I decided to open-source the engine component,
while keeping the game-specific components proprietary. The Siege Engine is that
open-sourced component.

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

In its current form, since about May 2017. Related work goes back much further.

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
that only a few game engines are written in Rust, and we have FAQ entries about them below.

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

* **cross-platform, somewhat**: We support Microsoft Windows and Linux. We expect to be able
to support MacOS (if Vulkan becomes available there) and Android. We are unlikely to support
consoles, but never say never.

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

### Why not use C++ or C#?

We think that the rust language simply offers a better deal: see
[What is the Rust language?](#what-is-the-rust-language).

C++ is common in game engine development, however. Epic Games' Unreal Engine, for
example, is written in C++. By moving to rust, however, we do not need to leave all that
legacy code behind. Rust programs can link via to any program that honors the C ABI
(as defined by the operating system), including to C++ libraries with that expose
extern "C" functions.

C# has another set of language issues I could get into, much of which it shares
with Java. But an even bigger issue is that C# is strongly tied into .NET and the
Microsoft Windows family of operating systems, making it "vendor locked."

C# is used by the popular Unity engine as a scripting language, however Unity itself
is cross-platform and written in C++.

### How is this different from other rust-based game engines?

There are several other game engines in rust including piston, ggez, and unrust,
and this is not an exhaustive list. We try to look into each of them.

We actually do use some libraries from the piston engine such as `image` and
`ddsfile` (which we contributed). However, not the core engine itself, as we find
that we seem to be targeting different types of games. We are excited about
[dyon](https://github.com/PistonDevelopers/dyon) and plan to investigate it further.

`ggez` explicitly targets 2D games, and we are targetting 3D.

We are in communication with the developer of `unrust` and sharing what we can.
His engine explicitly targets the browser through WebGL and wasm, whereas ours
targets a desktop application for games where performance (especially network
performance) is paramount.

### What graphics library is this based on, and why?

Siege has a long history of shifting the underlying graphics library.

Originally we based off of vulkano. Vulkano follows the Rust philosophy, which is
that "as long as you don't use unsafe code you shouldn't be able to trigger
any undefined behavior." The Vulkan API is an incredibly unsafe API and it is
very difficult to comply with it, and much harder to write code that always
complies in all use cases. So Vulkano is very ambitious. It became quickly
apparent that vulkano was not ready yet, and wasn't always being developed as
actively as we had hoped.

We decided that instead of strict safety, we would rely on the Vulkan validation
layers and frequent reads of the Vulkan specification.

Several other crates were wrapping the Vulkan API in less ambitious ways,
hiding the unsafes and dealing with lifetimes and drop traits, but not
ensuring that all requirements of the Vulkan API were met. These include
`ash` and `dacite`.

We started off using ash, but we ran into a problem. A pernicious bug that
we were unable to find. We had put in a solid two weeks and were no closer
to the problem. It manifested as a change in rendering behavior whenever
different vulkan layers were used, and it manifested on completely different
hardware so it was not driver dependent. I filed a bug with the vulkan layers
but the Khronos group, try as they might, could not find the bug either.
The reigning theory was subtle memory corruption, and the likely culprit
was ash. Finally after about a month I decided to change underlying libraries
and switched to the dacite crate.

A year later and dacite is now stagnant. It also does some copies and
allocations at runtime that are not strictly necessary. So we are keen to
move on.

gfx-rs offers great promise giving access to multiple graphics APIs (vulkan,
direct3d, metal, WebGL, etc). However it is currently undergoing a major
refactor/upheaval (the low-level refactor). Also it remains to be seen how
much of the Vulkan functionality will be provided, and how much compromise
will be made.

We will probably change back to ash, since it is actively developed. But we are
putting off this decision for now.

### Why not use cgmath or nalgebra?  Why create yet another math crate?

This was an admitted mistake on our part. We didn't think it through. We only
thought "A math crate is small and easy, we can whip one of those up and have
easy control of it." What we didn't realize is that further on down the road,
our work would not as easily interoperate with other community work.

So we intend to change over to cgmath, which is the more popular of the two
and seems less wildly abstract than nalgebra.

### Why does this have its own UI library and not use an existing one?

The siege-engine UI library is very new and was developed to get something on the
screen quickly, without much regard to other libraries available. It is now about
time to look around for something more than the fledgling UI we currently have.

Conrod is on our radar.
However, [this issue](https://github.com/PistonDevelopers/conrod/issues/1103) leads
us to believe conrod (connie?) has made specific choices which do not align with
our goals, and thus may not be usable by the siege engine. Even if that turns out
to be the case, we hope to learn as much as we can from it.

A new crate xi-win-ui looks interesting.

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
