<!--

WARNING!! DON'T EDIT THE FILE README.md on the root of the project, that one is a GENERATED FILE!

You should just edit the source file at src/README.md - the one which stars with ## Three.js - 3D almost easy

-->

## Three.js - 3D almost easy



Lu&iacute;s Pinheiro @ [Avenue Code](http://www.avenuecode.com)

*lpinheiro@avenuecode.com*

Jul 17th, 2014

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

- Get it at [Three.js](http://threejs.org/).
- MIT Licensed.
- Open source.
- It's part of [Khronos Group](http://www.khronos.org/webgl/), not W3C.
- Setup a local environment for localy dev avoid many erros with same-origin policy;

----

## Getting Started :: Samples

- http://threejs.org/examples/webgl_materials_cubemap_balls_reflection.html
- http://acko.net/
- http://www.chaostoperfection.com/
- http://hellorun.helloenjoy.com/

----

## Getting Started :: Markup

    <html lang="en">
        <head>
            <title>Getting starting into three.js</title>
            <meta charset="utf-8">
        </head>
        <body style="margin: 0;">
            <script src="js/three.min.js" >
            </script>
            <script>
                // Our 3D code will go here...
            </script>
        </body>
    </html>`

----

## Getting Started :: Concepts

- *Mesh* is a collection of Vertex, Edges and Faces that describe the surface, the shape, of any given object;
- *Vertex* is the corner of the object, where two or more faces and edges collide;
- *Edge* is a line that connects two vertex, or the boundary in a circle;
- *Face* is the area inside edges or individual surface of a solid object;
- *Asset* is any digital content, usually artistic, that includes the 'right to use it';

----

## Getting Started :: Utility

- *Detector.js*, included in three.js, it detects if the WebGl is supported. Similar to Modernizr.
- *Stats.js* it's a javascript performance monitor, created by the same author as Three.js.

---

## Setting up

- To be able the display anything you need, at least, three things:
1. A scene
2. A renderer
3. A camera

----

## Setting up :: Scene

- *Scene* is where every object is added to be rendered.
        var scene = new THREE.Scene();

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

----

## Setting up :: Camera

- *Camera* is how the scene will be displayed.
        //  set some camera attributes
        var VIEW_ANGLE = 45,
            ASPECT = window.innerWidth / window.innerHeight,
            NEAR = 0.1,
            FAR = 10000,
        //  create the camera
            camera = new THREE.PerspectiveCamera(VIEW_ANGLE, ASPECT, NEAR, FAR);
        // the camera starts at 0,0,0 so pull it back
        camera.position.z = 300;


---

## Models and Materials

- Is really hard to create models with vanilla javascript;
- Commonly models are made in 3D modeling tools as Maya, Blender, SketchUp, etc;
- If you preferred tool don't export to any "ready-to-use" format, use *collada* or *object* format then go to the [Three.js online editor](http://threejs.org/editor/);
- Load your assets using the appropriate loader;
        var loader = new THREE.JSONLoader();
- Built-ins Geometry and Material;
        var geometry = new THREE.BoxGeometry(1,1,1),
            material = new THREE.MeshLambertMaterial( { color: 0x00ff00 } ),
            mesh = new THREE.Mesh( geometry, material );

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

- Build any Scene that uses all concepts showed in this talk.