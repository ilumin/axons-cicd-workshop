---
section: Deploy Frontend
layout: cover
---

## Deploy Frontend

---

# Fork Frontend Repository 

- Go to [https://github.com/ilumin/yummy-list](https://github.com/ilumin/yummy-list)
- Click "Fork"
- Fork new repository

---

# Initiate Firebase Project

<div class="grid grid-cols-2 gap-4">
<div>

> **Prerequisite**  
> - Firebase account

Initialize Firebase project on local project  

```sh
# install firebase cli
npm i -g firebase-tools

# initiate Firebase project 
# with hosting & GitHub Action support
firebase init hosting:github
```

</div>
<div>

Firebase cli will generate GitHub workflows and its configurations  
- `.github/workflows/firebase-hosting-merge.yml`
- `.github/workflows/firebase-hosting-pull-request.yml`
- `.firebaserc`

</div>
</div>

---

# Enter Firebase Config

> ? For which GitHub repository would you like to 
>   set up a GitHub workflow?  
> `your repository name`

<br />

> ? Set up the workflow to run a build script 
>   before every deploy?  
> `Y` 

<br />

> ? What script should be run before every deploy?   
> `npm ci && npm run build`

<br />

> ? Set up automatic deployment to your site's 
>   live channel when a PR is merged?  
> `Y` 

<br />

> ? What is the name of the GitHub branch associated 
>   with your site's live channel?  
> `main`

---

# Modify GitHub Workflows

Edit file `.github/workflows/firebase-hosting-merge.yml` and `.github/workflows/firebase-hosting-pull-request.yml`

```yml {monaco-diff} {line:true, startLine:12}
steps:
  - uses: actions/checkout@v3
  - run: npm ci && npm run build
  - uses: FirebaseExtended/action-hosting-deploy@v0
~~~
steps:
  - uses: actions/checkout@v3
  - run: npm ci
  - run: VITE_API_URL=${{ secrets.VITE_API_URL }} npm run build
  - uses: FirebaseExtended/action-hosting-deploy@v0
```

<br />

> Change from `npm ci && npm build` to ...
> - `npm ci`
> - `VITE_API_URL=${{ secrets.VITE_API_URL }} npm run build`  
>   attach environment variable on build

Then commit and push

---

# Setup Pipeline

<div class="grid grid-cols-2 gap-4">
<div>

- Add secrets in **Actions secret and variables**  
  (Settings > Secret and variables > Actions)
- Click "New repository secret"
  - Add `VITE_API_URL` with the backend API
- Then run pipeline again
- Check result on `Run FirebaseExtended/action-hosting-deploy@v0`

</div>
<div>

![Check deployment](/frontend-deploy-1.png)

</div>
</div>

<!-- 
- หลังจากที่ push code ขึ้นมา เราจะเจอ build failed เพราะว่าเรายังไม่ได้ set secrets
- เมื่อ deploy เสร็จ เข้าไปดูรายละเอียดใน step `Run FirebaseExtended/action-hosting-deploy@v0`
  - scroll ไปด้านล่างจะเห็น URL ของเราที่ Firebase สร้างให้
  - โดยปกติจะเป็น `firebase-project.web.app`
-->

--- 

# Test

![Running App](/overview-2.png)