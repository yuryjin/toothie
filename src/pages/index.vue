<template>
  <div>

    <div class="main-component main-view"  :style="{'background-color':backgroundColor}">
      <div id="main" class="main" :style="{'background-color':backgroundColor}"></div>

      <div class="menu left-menu">
        <label for="exampleInputEmail1" class="form-label">Цвет фона</label>
        <div class="mb-3">
          <button class="btn btn-light" v-on:click="changeColor('#999999')">Серый</button>
          <button class="btn btn-light" v-on:click="changeColor('#ffffff')">Белый</button>
          <button class="btn btn-light" v-on:click="changeColor('#000000')">Чёрный</button>
        </div>
        <h4>Выбор зуба</h4>
        <div class="mb-3 text-center">
          <select class="form-control" style="margin-left: auto; margin-right: auto; width: 80%" aria-label="Default select example" v-model="selectedTooth">
            <option>1</option>
            <option>2</option>
            <option>3</option>
            <option>4</option>
            <option>5</option>
            <option>6</option>
            <option>7</option>
            <option>8</option>
            <option>9</option>
            <option>10</option>
            <option>11</option>
            <option>12</option>
          </select>
          <p>Выбранный зуб - {{selectedTooth}}</p>
        </div>
      </div>

      <div class="menu right-menu">
        <div class="mb-3">
          <button type="submit" class="btn btn-primary" style="background-color: red; position: absolute; bottom: 5%; left: 40%"
          v-on:click="renderView = !renderView">Выйти</button>
        </div>
      </div>
    </div>

        <div class="main-component main-menu" v-if="renderView == false" :style="{'background-color':backgroundColor}">
      <div class="main-menu-options">
        <button class="mt-5 btn btn-primary" v-on:click="renderView = !renderView">Включить</button>
      </div>
    </div>

    <!--
    <div class="main-component main-menu" v-else :style="{'background-color':backgroundColor}">
      <div class="main-menu-options">
        <button class="mt-5 btn btn-primary" v-on:click="renderView = !renderView">Включить</button>
      </div>
    </div>
    -->

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

  var degree = Math.PI / 180;

  const scene = new Three.Scene();
  //scene.background = new Three.Color(0xdddddd);
  const camera = new Three.PerspectiveCamera(5, window.innerWidth / window.innerHeight, 0.1, 1000);

  // Camera positioning
  camera.position.z = -90;
  camera.position.y = 100;
  camera.rotation.x = -10 * degree;
  //camera.lookAt(new Three.Vector3(0,0,0));

  // Ambient light (necessary for Phong/Lambert-materials, not for Basic)
  var ambientLight = new Three.AmbientLight(0xffffff, 1);
  scene.add(ambientLight);


  //camera.position.z = 1;
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
        mesh: null,

        renderView: false,
        backgroundColor: '#999999',
        selectedTooth: '1'
      }
    },
    methods: {
      changeColor: function (color) {
        this.backgroundColor = color;
      },
      init: function () {
        let container = document.getElementById('main');



        renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(renderer.domElement);

        const controls = new OrbitControls(camera, renderer.domElement);
        const loader = new STLLoader();
        const objloader = new OBJLoader();

        loader.load('./stl/zub2.stl', function (geometry) {
          var material = new Three.MeshLambertMaterial({
            color: 0xFFFFFF,
            specular: 0x111111,
            shininess: 200
          });
          var mesh = new Three.Mesh(geometry, material);
          mesh.position.set(0, 0, 0);
          scene.add(mesh);
        });

        /*
        objloader.load(
          // resource URL
          './stl/zubi.obj',
          // called when resource is loaded
          function (object) {

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
        */


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

  .main-component {
    margin: 0;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
  }

  .main-menu-options {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    border: 1px gray solid;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    border-radius: 5px;
    width: 400px;
    height: 200px;
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