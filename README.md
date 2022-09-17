# awaslaku
URL: https://github.com/grafana/grafana/blob/main/contribute/developer-guide.md

## Requirements
    - Git
    - Go (see go.mod for minimum required version)
    - Node.js (Long Term Support)
    - Yarn
    ```
      $ sudo corepack enable
    ```
    - [make]
    - [gcc]
    
## Clone Grafana

git clone https://github.com/grafana/grafana.git

## Build

### Frontend

YARN_CHECKSUM_BEHAVIOR=update yarn install --immutable

yarn start


### Backend

make run

Access at default URL http://localhost:3000
Login/password: admin/admin

## Modification

grep -r -l from Grafana root directory

e.g.:
```
$ grep -r -l "Welcome to Grafan"
emails/signup_started.html
emails/welcome_on_signup.txt
emails/welcome_on_signup.html
emails/signup_started.txt
dashboards/default.json
app/core/components/Signup/SignupPage.test.tsx
app/core/components/Login/LoginPage.test.tsx
app/core/components/Branding/Branding.tsx
app/features/dashboard/components/ShareModal/SharePublicDashboard.tsx
app/features/dashboard/components/ShareModal/SharePublicDashboard.test.tsx
app/plugins/panel/welcome/Welcome.tsx
app/plugins/panel/gettingstarted/steps.ts
```

Case-0: removing "Library panels"
At menubar: pkg/api/index.go 
At sidebar: locales/en-US/messages.po

Case-1: change "Welcome to Grafana"
app/core/components/Branding/Branding.tsx
app/plugins/panel/welcome/Welcome.tsx
app/plugins/panel/gettingstarted/steps.ts

Case-2: changing Footer
app/core/components/Footer/Footer.tsx

Case-3: removing Footer
app/core/components/Page/Page.tsx

Case-4: removing "Stats and licensing"
At menubar and sidebar: pkg/services/licensing/oss.go

BUILD

Frontend

YARN_CHECKSUM_BEHAVIOR=update yarn install --immutable

mkdir plugins-bundled/external

export NODE_OPTIONS="--max-old-space-size=8192"

make build-js

Backend

make gen-go

make deps-go

make build-go  

List of files to be modified

<grafana>/pkg/api/index.go
    
<grafana>/pkg/services/licensing/oss.go
    
<grafana>/public/app/core/components/Branding/Branding.tsx
    
<grafana>/public/app/core/components/Footer/Footer.tsx
    
<grafana>/public/app/core/components/Page/Page.tsx
    
<grafana>/public/app/plugins/panel/gettingstarted/steps.ts
    
<grafana>/public/app/plugins/panel/welcome/Welcome.tsx
    
<grafana>/public/img/grafana_icon.svg
    
<grafana>/public/views/index.html
    
.. index-template.html

COMPILED DOWNLOAD
    
    https://drive.google.com/drive/folders/1eCyO6rL2iQV4aHJmWUqmn8wEU1la-dZc?usp=sharing
    
