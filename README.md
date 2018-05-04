# siege-engine

This crate is documentation/overview only.

The Siege Engine is an MMO Game Engine targetting the Vulkan API and written in the
Rust language.

## Example

Here is a screenshot from a game being developed using the Siege Engine:

![Example Thumb](/example_thumb.png)
[Click for larger image](/example.png)

## Goals

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

## News

I am starting to open-source the Siege Engine, an MMO Game Engine targeting the Vulkan API
written in the Rust language.

The main crates are (not yet published as of this writing):

* *siege-client*: A graphical game client, the biggest component.
* *siege-server*: A skeleton of a game server.
* *siege-net*: A network protocol connecting the two.

## Why? Why not just use Unreal Engine or Unity Engine?

1. Freedom from licensing restrictions
1. Platform independence
1. The numerous benefits of the Rust language
