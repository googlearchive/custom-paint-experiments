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
<style>
  #pu {
    --color:LightSteelBlue;
  }
</style>
<script>
  class MyPainter {
    static get inputProperties() { return ['--color']; }
    paint(ctx, geom, properties) {
      ctx.fillStyle = properties.get('--color').cssText;
      ctx.fillRect(0, 0, geom.width, geom.height);
    }
  }
  Painters.registerPaint('my-painter', MyPainter);
</script>
<paint-underlay id="pu" paint="my-painter" auto-update-geometry auto-update-style>
  <div slot=content>Hello, paint!</div>
</paint-underlay>
```
