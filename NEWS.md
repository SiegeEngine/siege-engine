# news

## 2018 May 10

* I have finished open sourcing all the code, and the example `siege-example-client` is
  available for people to try.

* I'm looking around at other crates, and I think the biggest impediment to integration
  with other people's game engines (piston, unrust, ggez, gfx-rs etc) is that I am using
  my own `siege-math` crate, which means that even if I create well-defined traits for
  interoperability, if they reference `siege-math` types, people will be unlikely to use
  them. So I either have to implement From between siege-math and cgmath and/or nalbegra,
  or I should look more closely and determine why I need my own math library.

## 2018 May 7

* I'm open sourcing the engine.  I have to extract my game from it, so it is
  rather rough around the enges still.
