# Siege Engine FAQ

### What is the Siege Engine?

The Siege Engine is an MMO Game Engine targetting the Vulkan API and written in the
Rust language.

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

While it is still a big project, it is no where near the scale of an MMO project.

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

### What is the Rust language?

Rust is a systems programming language that runs blazingly fast, prevents segfaults,
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

C# is the language used by the popular Unity engine.

### Why build yet another game engine?  Why not use Unreal Engine or Unity?

As mentioned above, those engines rely on languages that we do not prefer.
Further, they require commercial licensing. Additionally, they are vendor locked
to the Microsoft Windows family of operating systems.

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
else. In this way, the full Vulkan API is exposed and somewhat safe, but fully
usable immediately.

### Are these really the most frequently asked questions?

No. I have collected no statistics. This is just a convenient format to
disseminate information.