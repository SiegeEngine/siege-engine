![Example](/example.png)

# siege-engine-docs

The Siege Engine is an MMO Game Engine targetting the Vulkan API and written in the
Rust language.

This crate is overview documentation only. For API level documentation, see the individual
repositories themselves, and/or their rust documentation.

## [FAQ](/FAQ.md)

## [NEWS](/NEWS.md)

## Trying it out

The `siege-example-client` crate is an example usage of the engine. You can compile and run
that stand-alone if you wish, no configuration necessary.

The `siege-example-server` crate is the server part of the example. To use this:

1. First compile `siege-example-server`
2. Run its `generate_keypair` binary, and copy the pkcs8 file to some convenient location.
3. Configure the `siege.toml` file with the IP address and port that the server will listen on.
4. Configure your `siege-example-client` with both your server's IP address and your servers
   public key (the public key is an array of 32 u8s that was printed when you ran
   generate_keypair).
5. Now run the client, and it should connect to your server.

`siege-example-net` is also part of this example, and is the library that defines the
network packets for the example.

## Warnings

This engine has a lot of rough edges and sharp corners, poorly designed placeholder code
and gaps in functionality large enough for an ogre to fall through.

We think, however, that the general architecture is sound (e.g. that we wont have to
'start over' in order to fix anything).
