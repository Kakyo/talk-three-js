<!--

WARNING!! DON'T EDIT THE FILE README.md on the root of the project, that one is a GENERATED FILE!

You should just edit the source file at src/README.md - the one which stars with ## @@title

-->

## @@title



@@author @ [Avenue Code](http://www.avenuecode.com)

*@@email*

@@date

---

## Agenda

- Prerequisites
- Browser Compatibility
- Getting Started
- Setting up
- Models and Materials
- Let there be light
- I like to move it, move it
- Conclusion
- Learn More
- Challenge

---

## Prerequisites

- Advanced javascript
- Some 3D modeling
- Some Math knowledge

---

## Browser Compatibility

- Chrome, Firefox, Safari, IE (11+)
- *NO* mobile support
- [Support table](http://caniuse.com/#search=webgl)

---

## Getting Started

- Get it at [Three.js](http://threejs.org/);
- Or install in *node* with
        $ npm install three;
- MIT Licensed and open source;
- Setup a local environment for local dev avoid many errors with same-origin policy;
- WebGL is part of [Khronos Group](http://www.khronos.org/webgl/), not W3C;

----

## Getting Started :: Samples

- [Threejs.org - Reflection example](http://threejs.org/examples/webgl_materials_cubemap_balls_reflection.html)
- http://hellorun.helloenjoy.com/
- http://acko.net/
- http://www.chaostoperfection.com/

----

## Getting Started :: Markup

        <!doctype html>
        <html lang="en">
            <head>
                <title>Getting starting into three.js</title>
                <meta charset="utf-8">
            </head>
            <body style="margin: 0;">
                <div id="container"></div>
                <script type="text/javascript" src="js/three.min.js" ></ script>
                <script type="text/javascript">
                    // Our 3D code will go here...
                </ script>
            </body>
        </html>

----

## Getting Started :: Concepts

- *Asset* is any digital content, usually artistic, that includes the 'right to use' it;
- *Mesh* is a collection of Vertex, Edges and Faces that describe the surface, the shape, of any given object;
- *Vertex* is the corner of the object;
- *Edge* is a line that connects two vertex;
- *Faces* are individual surfaces of a solid object;

![Mesh example](img/mesh.jpg)

----

## Getting Started :: Utility

- *Detector.js*, included in three.js, it detects if the WebGl is supported. Similar to Modernizr.
- *Stats.js* it's a javascript performance monitor, created by the same author as Three.js.

---

## Setting up

- To be able to the display anything you need, at least, three things:

  1. A scene
  1. A camera
  1. A renderer

----

## Setting up :: Scene

- *Scene* is where every object is added to be rendered.
        var scene = new THREE.Scene();

----

## Setting up :: Camera

- *Camera* is how the scene will be displayed.
        var VIEW_ANGLE = 45, NEAR = 0.1, FAR = 10000,
            ASPECT = window.innerWidth / window.innerHeight,
            camera = new THREE.PerspectiveCamera(VIEW_ANGLE, ASPECT, NEAR, FAR);
        // the camera starts at 0,0,0 so pull it back
        camera.position.z = 300;

![Example of camera parameters](img/cam-param.jpg)

----

## Setting up :: Renderer

- *Renderer* is which tech will be used to display the scene;
- WebGl, Canvas e SVG renderers are built-in in Three.js;

        var renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth , window.innerHeight);

- If you enable Detector.js, you could use some fallback;

        var renderer = Detector.webgl
            ? new THREE.WebGLRenderer()
            : new THREE.CanvasRenderer();

- Run the render method to actually display the scene.
        renderer.render(scene, camera);


---

## Models and Materials

- Built-ins Geometry and Material;
        var geometry = new THREE.BoxGeometry(1,1,1),
            material = new THREE.MeshLambertMaterial( { color: 0x00ff00 } ),
            mesh = new THREE.Mesh( geometry, material );
- It's really hard to create models with vanilla javascript;
- Commonly models are made in 3D modeling tools as Maya, Blender, SketchUp, etc;
- Load your assets using the appropriate loader;
        var loader = new THREE.JSONLoader();
- If your preferred tool don't export to any "ready-to-use" format, use *collada* or *object* format then go to [Three.js online editor](http://threejs.org/editor/);

---

## Let there be light

- There are many built-in light in Three.js
- In *ambient* light every face of every object in the scene receive the same amount of light;
- In *directional* light an light ray shines to the infinite;
- The *point* light is placed in one point and shines in all directions;
        // create a point light
        var pointLight = new THREE.PointLight(0xFFFFFF);
        pointLight.position.z = camera.position.z;
        pointLight.position.x = pointLight.position.y = 75;
        // add to the scene
        scene.add(pointLight);

---

## I like to move it, move it

- The renderer will render the current state of each object currently in the scene;
        (function render() {
            requestAnimationFrame(render);

            mesh.rotation.x += 0.01;
            mesh.rotation.y += 0.01;

            renderer.render(scene, camera);
        }());

- *requestAnimationFrame* should be used with caution due to cross-browser issues, [Paul Irish's shim](http://paulirish.com/2011/requestanimationframe-for-smart-animating/) is highly recommend;

---

## Conclusion

- Three.js is a really simple yet powerful library. Like jQuery, for 3D.
- The library allow people with small knowledge in WebGl to build even complex 3D applications;
- We just scratch the surface, Three.js is a gold mine waiting for be explored;

---

## Learn more

- [Three.js Samples](http://threejs.org/)
- [3D Modeling courses](http://www.digitaltutors.com/subject/3d-tutorials)

---

## Challenge

  1. Download/Create a model, like a house, then *import*, apply a *texture* and add some *lighting*;
  1. Create a awesome Space-ship that you can *control* on the keyboard/mouse and *shoot* deathly missiles;
  1. Build a new legendary screen-saver with abstract *shapes* and random *animations* or *glowing* lights;
  1. Build any scene that uses *all concepts* showed in this talk with *camera* control;