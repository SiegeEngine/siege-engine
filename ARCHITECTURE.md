# Siege Engine Architecture

## Client Architecture

```code
  Your Client
  +- Siege Render
  +- Your Networking
  |  +-- Siege Net
  +- (maybe) siege-math
  +- (maybe) siege-color
```

Your client will want to instantiate a siege-render Renderer, plugin some
plugins, and run it.

You'll need a networking library that probably depends on siege-net. This extra
layer is required since you'll want to be extending the packet type, and will
surely have your own network related code.

## Server Architecture

```code
  Your Server
  +- Your Networking
  |  +-- Siege Net
  +- (maybe) siege-math
```

Essentially like client architecture, but simpler. Utilise the same custom
networking library that you created for the client.

## Asset Creation

### Basic example meshes

```code
   siege-mesh/cube_standard -> cube_standard.mesh
```

Forthcoming siege-render standard mesh plugin will utilize this.

### Fonts

```code
  somefont.ttf --siege_font_create-> (somefont.bin, somefont.dds)
```

Forthcoming siege-render UI plugins will utilize these.
