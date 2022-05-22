# How to use babylonjs
## Step 1: Create a Babylon scene
All projects using the Babylon.js Engine need a scene with a camera and a light added
```javascript
const createScene = () => {
    const scene = new BABYLON.Scene(engine);

    const camera = new BABYLON.ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 3, new BABYLON.Vector3(0, 0, 0));
    camera.attachControl(canvas, true);

    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0));

    const box = BABYLON.MeshBuilder.CreateBox("box", {});

    return scene;
}
```
Having created our box we can save, or export, the scene from within the playground by selecting the Inspector.

<img src = "https://doc.babylonjs.com/_next/image?url=%2Fimg%2Fgetstarted%2Fpgpartmenu.png&w=1920&q=75"/>

followed by Tools and choose which type to export, the .babylon format or the GLB format.

<img src = "https://doc.babylonjs.com/_next/image?url=%2Fimg%2Fgetstarted%2Fexport.png&w=1920&q=75"/>

## Step 2: Enhancing Your Website
In order to use the Viewer you need to add its code to your HTML page in a \<script\> element
```html
<script src="https://cdn.babylonjs.com/viewer/babylon.viewer.js"></script>
```
Once this is added you place the <babylon> element in an appropriate container and points its model attribute to the file source.
```html
<babylon model="Path to File"></babylon>
```

## Tips: A Web Application Template
Babylonjs template
```javascript
var createScene = function() {
    var scene = new BABYLON.Scene(engine);

    // Add a camera to the scene and attach it to the canvas
    // Add a lights to the scene

    //Your Code

  return scene;
};
```
Html page template
```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">

    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
        <title>Babylon Template</title>

        <style>
            html, body {
                overflow: hidden;
                width: 100%;
                height: 100%;
                margin: 0;
                padding: 0;
            }

            #renderCanvas {
                width: 100%;
                height: 100%;
                touch-action: none;
            }
        </style>
        
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <!-- allow you to import models into your scene -->
        <script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>
        <!-- allow you to use a touch screen -->
        <script src="https://code.jquery.com/pep/0.4.3/pep.js"></script>
    </head>

   <body>

	<canvas id="renderCanvas" touch-action="none"></canvas> <!-- touch-action="none" for best results from PEP -->

	<script>
        const canvas = document.getElementById("renderCanvas"); // Get the canvas element
        const engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine

        // Add your code here matching the playground format

        const scene = createScene(); //Call the createScene function

        // Register a render loop to repeatedly render the scene
        engine.runRenderLoop(function () {
                scene.render();
        });

        // Watch for browser/canvas resize events
        window.addEventListener("resize", function () {
                engine.resize();
        });
	</script>

   </body>

</html>
```
