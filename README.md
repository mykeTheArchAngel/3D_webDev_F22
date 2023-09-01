# Web 3D Tutorial

_Blender to Web3D as fast as possible_

![Preview](/public/preview.png)

This repo is meant to accompany a tutorial series on Youtube that starts here: https://youtu.be/1BvLpt7egss

As the course advances I'll add scripts here to make some tasks easier and grow this to be a Blender to Web toolkit.

Discuss here on Discord: https://discord.gg/5rTCdzpKnj

### Requirements:

- [Node.js](https://nodejs.org/en/download/)
- [VS Code](https://code.visualstudio.com/download) , to follow along with the tutorial
- [Blender](https://www.blender.org/download/) , We are focusing on Blender to Web
### Resources:

- [Flying Apartment Asset](https://www.cgtrader.com/3d-models/exterior/cityscape/cyberpunk-flying-apartment)
- [React Three Fiber](https://docs.pmnd.rs/react-three-fiber/): Three.js Renderer
- [Drei](https://github.com/pmndrs/drei): React Three Fiber Helpers
- [Three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene): 3D Engine
- [Vite](https://vitejs.dev/guide/): Static Web Server
- [CodeSandbox](https://codesandbox.io/docs/configuration): Online Prototyping Container (optional)

### Installation

```
npm install
```

### Getting Started

1. Open a model in Blender you want to publish (places like [CG Trader](https://www.cgtrader.com/) are a good start)
2. Export to `public/model.glb`
3. open a terminal to `/src` directory
4. run `npx gltfjsx ../public/model.glb`
5. rename the new `Model.js` to `Model.jsx`
6. run `npm run dev` from terminal
7. look at what you did, tune and repeat
### Scripts

```
npm run dev
npm run build
npm run preview
npm run sandbox
```
### detailed notes for Blender -> Web3D

#### Models

1. Import your model (I got an stl from printables.com)
2. Models CAN be created progmatically if that makes sense to do.
3. Models can come from multiple files
4. test things with gltf export NOT glb
5. Split parts
   1. by whats separate
   2. by materials
   3. select faces + more technique
6. Reduce geometry
   1. Remove unnecessary components for 3d printing
   2. highlight and dissolve unnecessary vertices
   3. limited dissolve intricate parts
7. join parts and set origins logically for use later
8. rename parts to what's easy to recognize
9. parent objects based on what needs to move together
10. add materials (detailed separately)
11. add lights (detailed separately)


#### Materials

1. Materials in Blender
2. UVs
   1. bulk script on Gist
3. GLTF export materials
4. BSDF Material
5. Baking Materials
6. Materials in R3F
   1. Special materials
   2. Cloning
   3. Modifying
   4. Unique capabilities

#### Lighting

1. more lights == slower performance
2. use '-s' in gltfjsx transform
   1. include drei Instances if using -i
3. add these properties to each light: castShadow shadow-mapSize={[2048, 2048]} shadow-bias={-.0000001} in Model.jsx
4. adjust intensity values and shadow-bias
5. add castShadow receiveShadow to instance Merged tag in Model.jsx 

#### Animating

1. useFrame lerp https://medium.com/@zmommaerts/animate-a-camera-in-react-three-fiber-7398326dad5d
2. Theater js https://www.theatrejs.com/
3. useAnimations:
   1. naming is everything!
   2. NLA tracks are a pain
   3. can group virtually
   4. onClick interactions
   5. play forward and backward. 
4. Spring https:/docs.pmnd.rs/react-three-fiber/tutorials/using-with-react-spring
5. Drei Animations