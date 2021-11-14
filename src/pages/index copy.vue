<template>
  <div id="main" class="main">


  </div>
</template>

<script>
/*
import { useUserStore } from '~/stores/user'

const user = useUserStore()
const name = ref(user.savedName)

const router = useRouter()
const go = () => {
  if (name.value)
    router.push(`/hi/${encodeURIComponent(name.value)}`)
}

const { t } = useI18n()
*/

import * as Three from 'three'
import * as orbitControls from 'three-orbitcontrols'
import * as STLLoader from 'three-stl-loader'


/*
const container = document.getElementById('main');

const camera = new Three.PerspectiveCamera(70, window.innerWidth/window.innerHeight, 0.01, 10);
camera.position.z = 1;
const scene = new Three.Scene();
//scene.background = new THREE.Color(0xdddddd);
let geometry = new Three.BoxGeometry(0.2, 0.2, 0.2);
let material = new Three.MeshNormalMaterial();
const mesh = new Three.Mesh(geometry, material);
scene.add(mesh);
const renderer = new Three.WebGLRenderer({antialias: true});
*/

/*
const renderer = new Three.WebGLRenderer({antialias: true});
renderer.setSize(window.innerWidth, window.innerHeight);
container.appendChild(renderer.domElement);
*/

/*

const scene = new Three.Scene();
const camera = new Three.PerspectiveCamera(70, window.innerWidth/window.innerHeight, 0.01, 10);
camera.position.z = 1;
const renderer = new Three.WebGLRenderer({antialias: true});
let geometry = new Three.BoxGeometry(0.2, 0.2, 0.2);
let material = new Three.MeshNormalMaterial();
const mesh = new Three.Mesh(geometry, material);

*/

/*
const scene = new Three.Scene();
const camera = new Three.PerspectiveCamera(70, window.innerWidth/window.innerHeight, 0.01, 10);
camera.position.z = 1;
const renderer = new Three.WebGLRenderer({antialias: true});
let geometry = new Three.BoxGeometry(0.2, 0.2, 0.2);
let material = new Three.MeshNormalMaterial();
const mesh = new Three.Mesh(geometry, material);
scene.add(mesh);
*/



export default {
  name: 'ThreeTest',
  data() {
    return {
      camera: null,
      scene: null,
      renderer: null,
      mesh: null
    }
  },
  methods: {
    init: function() {

        /*
        let container = document.getElementById('main');

        this.camera = new Three.PerspectiveCamera(70, window.innerWidth/window.innerHeight, 0.01, 10);
        this.camera.position.z = 1;

        this.scene = new Three.Scene();
        //scene.background = new THREE.Color(0xdddddd);

        let geometry = new Three.BoxGeometry(0.2, 0.2, 0.2);
        let material = new Three.MeshNormalMaterial();

        this.mesh = new Three.Mesh(geometry, material);
        this.scene.add(this.mesh);

        this.renderer = new Three.WebGLRenderer({antialias: true});
        this.renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(this.renderer.domElement);
        */

        let container = document.getElementById('main');

        this.camera = new Three.PerspectiveCamera(70, window.innerWidth/window.innerHeight, 0.01, 10);
        this.camera.position.z = 1;

        this.scene = new Three.Scene();
        //scene.background = new THREE.Color(0xdddddd);

        let geometry = new Three.BoxGeometry(0.2, 0.2, 0.2);
        let material = new Three.MeshNormalMaterial();

        this.mesh = new Three.Mesh(geometry, material);
        this.scene.add(this.mesh);

        this.renderer = new Three.WebGLRenderer({antialias: true});
        this.renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(this.renderer.domElement);

        this.renderer = new Three.WebGLRenderer({antialias: true});
        this.renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(this.renderer.domElement);

        this.renderer.render(this.scene, this.camera);

        /*
        let container = document.getElementById('main');

        

        renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(renderer.domElement);
        
        renderer.render(scene, camera);
        */

        /*
        this.mesh = new Three.Mesh(geometry, material);
        this.scene.add(this.mesh);

        this.renderer = new Three.WebGLRenderer({antialias: true});
        this.renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(this.renderer.domElement);
        */

    },
    animate: function() {
        requestAnimationFrame(this.animate);
        //this.mesh.rotation.x += 0.01;
        //this.mesh.rotation.y += 0.02;
        //this.renderer.render(this.scene, this.camera);


        /*
        mesh.rotation.x += 0.01;
        mesh.rotation.y += 0.02;
        renderer.render(scene, camera);
        */
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
</style>

