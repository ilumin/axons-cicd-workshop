---
section: Deploy Backend
layout: cover
---

## Deploy Backend

---

# Fork Backend Repository

<div class="grid grid-cols-2 gap-4">
<div>

- Go to [https://github.com/natchanonpor/backendNestjs](https://github.com/natchanonpor/backendNestjs)
- Click "Fork"
- Fork new repository

</div>
<div>

<div class="relative">
  <div class="absolute left-0 top-0" v-click="[1,2]"><img src="/backend-1.png" alt="click fork" /></div>
  <div class="absolute left-0 top-0" v-click="[2,3]"><img src="/backend-2.png" alt="set repository name" /></div>
</div>

</div>
</div>

---

# Setup Pipeline

<div class="grid grid-cols-2 gap-4">
<div>

- Add secrets in **Actions secret and variables**  
  (Settings > Secret and variables > Actions)
- Click "New repository secret"
  - Add `DOCKER_USERNAME`
  - Add `DOCKER_PASSWORD`
  - Add `DOCKER_IMAGE`

</div>
<div>

<div class="relative">
  <div class="absolute left-0 top-0" v-click="[0,1]"><img src="/backend-3.png" alt="secret management" /></div>
  <div class="absolute left-0 top-0" v-click="[1,2]"><img src="/backend-4.png" alt="add DOCKER_USERNAME" /></div>
  <div class="absolute left-0 top-0" v-click="[2,3]"><img src="/backend-5.png" alt="add DOCKER_PASSWORD" /></div>
  <div class="absolute left-0 top-0" v-click="[3,4]"><img src="/backend-6.png" alt="add DOCKER_IMAGE" /></div>
  <div class="absolute left-0 top-0" v-click="4"><img src="/backend-7.png" alt="all secret" /></div>
</div>

</div>
</div>

---

# Run Pipeline

<div class="grid grid-cols-2 gap-4">
<div>

- Goto **Actions** tab
- Click "I understand ..."  
  Shows GitHub actions dashboard
- Select "Docker Image CI"
- Click "Run workflow" button  
  Wait for result
- Check Docker hub at [https://hub.docker.com](https://hub.docker.com)

</div>
<div>

<div class="relative">
  <div class="absolute left-0 top-0" v-click="[0,1]"><img src="/pipeline-1.png" alt="ok" /></div>
  <div class="absolute left-0 top-0" v-click="[1,2]"><img src="/pipeline-2.png" alt="dashboard" /></div>
  <div class="absolute left-0 top-0" v-click="[2,3]"><img src="/pipeline-3.png" alt="run workflow" /></div>
  <div class="absolute left-0 top-0" v-click="[3,4]"><img src="/pipeline-4.png" alt="running" /></div>
  <div class="absolute left-0 top-0" v-click="[4,5]"><img src="/pipeline-5.png" alt="done" /></div>
  <div class="absolute left-0 top-0" v-click="[5,6]"><img src="/pipeline-6.png" alt="detail 1" /></div>
  <div class="absolute left-0 top-0" v-click="[6,7]"><img src="/pipeline-7.png" alt="detail 2" /></div>
  <div class="absolute left-0 top-0" v-click="7"><img src="/pipeline-8.png" alt="docker hub" /></div>
</div>

</div>
</div>

---

# Deployment

<div class="grid grid-cols-2 gap-4">
<div>

- Go to [https://labs.iximiuz.com/playgrounds/docker/](https://labs.iximiuz.com/playgrounds/docker/)  
  (might need to connect with GitHub account)
- Start Docker container  
  ```sh
  docker run -d -p 3000:3000 {{DOCKER_IMAGE}}
  ```
- Enable public link
- Config public link
- Copy link (use it for frontend variable)

</div>
<div>

<div class="relative">
  <div class="absolute left-0 top-0" v-click="[0,1]"><img alt="Docker playground" src="/backend-deployment-0.png"  /></div>
  <div class="absolute left-0 top-0" v-click="[1,2]"><img alt="Enter terminal" src="/backend-deployment-1.png"  /></div>
  <div class="absolute left-0 top-0" v-click="[2,3]"><img alt="Start Docker container" src="/backend-deployment-2.png" /></div>
  <div class="absolute left-0 top-0" v-click="[3,4]"><img alt="Enable public link" src="/backend-deployment-3.png" /></div>
  <div class="absolute left-0 top-0" v-click="[4,5]"><img alt="Config link" src="/backend-deployment-4.png" /></div>
  <div class="absolute left-0 top-0" v-click="5"><img alt="Get link" src="/backend-deployment-5.png" /></div>
</div>

</div>
</div>

<!-- 
- get link https://657137c3d838e5a30ddc7ed5-4377f3.node-c9a5.iximiuz.com 
- use it as variable for frontend
-->

---

# Test

<div class="grid grid-cols-2 gap-4">
<div>

- Go to [https://httpie.io/app](https://httpie.io/app)  
  (Or Postman, if you like)
- `GET /`  
  (Verified that it's `{ "ok": true }`)
- `POST /todos` with JSON body  
  ```json
  {
    "title": "Yummy"
  }
  ```
- `GET /todos`

</div>
<div>

<div class="relative">
  <div class="absolute left-0 top-0" v-click="[0,1]"><img alt="OK" src="/backend-test-1.png"  /></div>
  <div class="absolute left-0 top-0" v-click="[1,2]"><img alt="POST todo" src="/backend-test-2.png" /></div>
  <div class="absolute left-0 top-0" v-click="2"><img alt="GET todo" src="/backend-test-3.png" /></div>
</div>

</div>
</div>