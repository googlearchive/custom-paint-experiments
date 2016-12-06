<!---
```
<custom-element-demo>
  <template>
    <link rel="import" href="paint-lib.html">
    <link rel="import" href="paint-underlay.html">
    <style>
      paint-underlay {
        display: inline-block;
        margin: 5px;
      }
      div[slot=content] {
        padding: 5px;
        width: 100px;
        height: 100px;
      }
    </style>
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<paint-underlay id=pu>
  <div slot=content>Hello, paint!</div>
</paint-underlay>
<script>
  class Painter {
    paint(ctx, geom, properties) {
      ctx.fillStyle = 'LightSteelBlue';
      ctx.fillRect(0, 0, geom.width, geom.height);
    }
  }
  var cp = new CanvasPainter({
    canvas: pu.$.underlay,
    painter: new Painter(),
  });
  cp.updateGeometry(pu);
  cp.repaint();
</script>
```
