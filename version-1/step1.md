---
section: Overview
layout: cover
---

## Overview

---

# Sequence Diagram

<!-- <img alt="Flow" src="/overview-1.png" class="w-md ma" /> -->
![Sequence diagram](/overview-1.png){class="w-md ma"}

---

# Example Application 

<div class="relative w-full">
  <div class="absolute left-0 top-0 w-full" v-click="[0,1]"><img alt="Yummy list" src="/overview-2.png" /></div>
  <div class="absolute left-0 top-0 w-full" v-click="[1,2]"><img alt="Adding yummy food" src="/overview-3.png" /></div>
  <div class="absolute left-0 top-0 w-full" v-click="[2,3]"><img alt="Added yummy food" src="/overview-4.png" /></div>
  <div class="absolute left-0 top-0 w-full" v-click="[3,4]"><img alt="Removing yummy food" src="/overview-5.png" /></div>
  <div class="absolute left-0 top-0 w-full" v-click="4"><img alt="Shows error" src="/overview-6.png" /></div>
</div>

---

# Run backend on local

Backend [github.com/natchanonpor/backendNestjs](https://github.com/natchanonpor/backendNestjs)

```sh
# clone source code from GitHub
git clone https://github.com/natchanonpor/backendNestjs.git axn-lab-backend && cd axn-lab-backend/

# copy environment variable
cp .env-example .env

# install dependencies
npm i 

# run migrate script 
npm run prisma:deploy

# start local backend service
npm run start:dev

# open api (expected response: {"ok":true})
curl localhost:3000
```

---

# Run frontend on local

Frontend: [github.com/ilumin/yummy-list](https://github.com/ilumin/yummy-list)

```shell
# clone source code from GitHub
git clone https://github.com/ilumin/yummy-list.git axn-lab-frontend && axn-lab-frontend/

# copy environment variables
cp .env-example .env

# install dependencies
npm i

# start local frontend service
npm run dev
```

<!-- 
- เปิดเล่น frontend ให้ดู
- สมมุติว่าเรา dev เสร็จแล้ว และเราต้องการจะ deploy
- เรามาดูว่า deployment flow เป็นอย่างไร
-->

---

![Backend deployment flow](/overview-7.png)

<!-- 
- โดยปกติเราจะ deploy ผ่าน pipeline script 
- hosting ที่ axons ใช้จะเป็นของ AWS ซึ่งจะใช้ทั้ง ECS, EKS
- แต่เนื่องจากข้อจำกัดในการสร้าง environment เราจะมา deploy บน docker lab แทน
-->

---

![Frontend deployment](/overview-8.png)

