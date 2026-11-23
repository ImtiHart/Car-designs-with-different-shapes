# WebGL 2D Car Renderer

A frontend graphics project exploring raw **WebGL** (without external libraries like Three.js). This repository contains three progressive iterations of a 2D car, demonstrating the transition from basic line drawing to solid shapes and finally to coordinate-based particle generation.

## 🎯 Project Overview

WebGL is a low-level API that interacts directly with the GPU. This project bypasses high-level drawing tools to manually define vertex buffers, write GLSL shaders, and render geometry. 

## 🗂️ The Three Iterations

| File | Description | WebGL Concepts Demonstrated |
|------|-------------|-----------------------------|
| `index1.html` | The wireframe draft. A basic 2D car outline drawn using lines. | `gl.LINES`, basic vertex buffers, simple shaders without uniforms. |
| `index2.html` | The solid model. A fully colored car using triangles. | `gl.TRIANGLES`, **Index Buffers** (`ELEMENT_ARRAY_BUFFER`), uniform variables for colors, and shader compilation error handling. |
| `index3.html` | The point-cloud model. A "pixel art" style car generated dynamically. | `gl.POINTS`, custom point sizing (`gl_PointSize`), and using JavaScript loops to procedurally generate vertex coordinates. |

## 🚀 How to Run

Because WebGL runs directly in the browser, no build tools or local servers are strictly required.
1. Clone the repository.
2. Double-click any of the `index.html` files to open them in Chrome, Firefox, or Edge.
3. Ensure your browser supports WebGL (all modern browsers do).

## 🧠 How It Works (Under the Hood)

1. **Vertex Shaders:** Calculates the final position of the car's parts on the screen.
2. **Fragment Shaders:** Assigns the exact color (e.g., red for the car body, green for the wheels) to the pixels.
3. **Buffer Binding:** Moves the JavaScript arrays (the coordinates of the car) over to the GPU memory (`gl.createBuffer()`).
4. **Draw Calls:** Executes `gl.drawElements` or `gl.drawArrays` to tell the GPU to paint the triangles or lines.

## 📈 Key Technical Takeaways
- **Transition to Index Buffers:** In `index2.html`, we moved from duplicating vertices for every triangle to using an `indices` array. This is a vital optimization technique in 3D graphics to save GPU memory.
- **Uniforms:** In `index2.html` and `index3.html`, we pass a `color` uniform from JavaScript to the shader, allowing us to reuse the same shader program to paint different parts of the car different colors.
- **Error Handling:** `index2.html` introduces a `createShader` function that checks `gl.COMPILE_STATUS` and logs errors, which is a best practice in graphics programming.

## ⚠️ Known Limitations / Next Steps

- **Static Rendering:** The car currently draws once and sits still. The next step would be to add an animation loop (`requestAnimationFrame`) to make the car drive or spin.
- **2D Only:** These files use a 2D coordinate system. Extending this to 3D would involve adding a Z-axis and implementing camera matrices (projection and view).
- **Procedural Generation:** In `index3.html`, the car is made of dots. A future update could add physics to make the dots scatter or bounce.

## 📄 License
MIT (or your preferred license)
