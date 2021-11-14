<template>
  <div>

    <div id="main" class="main" style="background-color: #999999"></div>

    <div class="menu left-menu">
      <form class="m-4">
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label">Email address</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
          <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1">
        </div>
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label">Email address</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
          <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1">
        </div>
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label">Email address</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
          <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1">
        </div>
        <div class="mb-3 form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1">
          <label class="form-check-label" for="exampleCheck1">Check me out</label>
        </div>
        <button type="submit" class="btn btn-primary">Save</button>
      </form>
    </div>

    <div class="menu right-menu">
      <form class="m-4">
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label">Email address</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
          <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1">
        </div>
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label">Email address</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
          <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1">
        </div>
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label">Email address</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
          <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
        </div>
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1">
        </div>
        <div class="mb-3 form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1">
          <label class="form-check-label" for="exampleCheck1">Check me out</label>
        </div>
        <button type="submit" class="btn btn-primary">Save</button>
      </form>
    </div>

  </div>
</template>

<script>
  import * as Three from 'three'
  import * as OrbitControls from 'three-orbitcontrols'
  //import * as STLLoader from 'three-stl-loader'
  import {
    STLLoader
  } from 'three/examples/jsm/loaders/STLLoader.js';
  import {
    OBJLoader
  } from 'three/examples/jsm/loaders/OBJLoader.js';
  //import { LeftMenu } from './components/LeftMenu.vue'


  //var STLLoader = require('three-stl-loader')(THREE)

  const scene = new Three.Scene();
  //scene.background = new Three.Color(0xdddddd);
  const camera = new Three.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
  camera.position.z = 1;
  const renderer = new Three.WebGLRenderer({
    antialias: true,
    alpha: true
  });
  //let geometry = new Three.BoxGeometry(0.2, 0.2, 0.2);
  //let material = new Three.MeshNormalMaterial();
  //const mesh = new Three.Mesh(geometry, material);
  //scene.add(mesh);


  export default {
    name: 'ThreeTest',
    components: {
      //LeftMenu
    },
    data() {
      return {
        camera: null,
        scene: null,
        renderer: null,
        mesh: null
      }
    },
    methods: {
      init: function () {
        let container = document.getElementById('main');



        renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(renderer.domElement);

        const controls = new OrbitControls(camera, renderer.domElement);
        const loader = new STLLoader();
        const objloader = new OBJLoader();

        loader.load( './stl/zub2.stl', function ( geometry ) {
            var material = new THREE.MeshLambertMaterial( { color: 0xFFFFFF, specular: 0x111111, shininess: 200 } );
            var mesh = new THREE.Mesh( geometry, material );
            mesh.position.set( 0, 0, 0);
            scene.add( mesh );
        } );

        objloader.load(
          // resource URL
          './stl/zubi.obj',
          // called when resource is loaded
          function (object) {

            /*
            object.traverse( function ( child ) {
                      if ( child instanceof Three.Mesh ) {
                          child.material.ambient.setHex(0xFF0000);
                          child.material.color.setHex(0x00FF00);
                          }
                      } );
            */

           //object.traverse( function (obj) { if (obj.isMesh){ obj.material.color.set(0xFFB6C1); } } );

            /*
               object.traverse( function ( child ) {
                if ( child instanceof Three.Mesh )
                    child.material.color.setRGB (1, 0, 0);
            });
            */

            //let material = new Three.MeshNormalMaterial();
            //const mesh = new Three.Mesh(object, material);
            //scene.add(mesh);

            object.position.y = 0;
            

            scene.add(object);

          },
          // called when loading is in progresses
          function (xhr) {

            console.log((xhr.loaded / xhr.total * 100) + '% loaded');

          },
          // called when loading has errors
          function (error) {

            console.log('An error happened');

          }
        );


        //renderer.render(scene, camera);
      },
      animate: function () {
        requestAnimationFrame(this.animate);
        //mesh.rotation.x += 0.01;
        //mesh.rotation.y += 0.02;
        renderer.render(scene, camera);
      }
    },
    mounted() {
      this.init();
      this.animate();
    }
  }
</script>

<style scoped>
  .main {
    margin: 0;
  }

  .menu {
    position: absolute;
    background-color: white;
    width: 400px;
    height: 800px;
    border-radius: 2%;
  }

  .left-menu {
    top: 10%;
    left: 10%;
  }

  .right-menu {
    top: 10%;
    right: 10%;
  }
</style>