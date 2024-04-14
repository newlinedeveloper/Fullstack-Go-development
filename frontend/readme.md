### Frontend development

### prerequisites


```
node js installation  

https://nodejs.org/en/download/package-manager/

node version: v18 LTS

node --version

npm --version


npm i create-react-app - optional


```

### Create React js application

```
npx create-react-app web-app

cd web-app

npm run start

```


### Install Required Packages

```
npm install antd axios 

```


### Project structure

```
.
└── src/
    ├── Components/
    │   └── Models/
    │       ├── AddMemberModal.js
    │       └── EditMemberModal.js
    ├── Pages/
    │   └── Dashboard/
    │       └── index.js
    ├── services/
    │   ├── AxioInstance.js
    │   └── Member.js
    ├── App.js
    ├── App.css
    ├── index.js
    └── index.css

```

### Create .env file in src folder

```
REACT_APP_API_URL=http://localhost:8000

```


### Add Api integration functionalities

** create AxiosInstance.js file in Services folder**

```
import axios from "axios";

export const AxiosInstance = axios.create({
    baseURL: process.env.REACT_APP_API_URL
});

```

** create Member.js file in Services folder**

```
import { AxiosInstance } from "./AxiosInstance";

const config = {
    headers: {
        "Content-Type": "application/json",
    }
}

export const getAllMembersApi = async () => {
    try {
        const response = await AxiosInstance.get("/members", config)
        return response;
    } catch (error) {
        console.log(error)
        return error
    }
}

export const getMemberApi = async (id) => {
    try {
        const response = await AxiosInstance.get(`/member/${id}`, config)
        return response;
    } catch (error) {
        console.log(error)
        return error
    }
}

export const createMemberApi = async (data) => {
    try {
        const response = await AxiosInstance.post("/member", data, config)
        return response;
    } catch (error) {
        console.log(error)
        return error
    }
}


export const updateMemberApi = async (id, data) => {
    try {
        const response = await AxiosInstance.put(`/member/${id}`,data, config)
        return response;
    } catch (error) {
        console.log(error)
        return error
    }
}

export const deleteMemberApi = async (id) => {
    try {
        const response = await AxiosInstance.delete(`/member/${id}`,config)
        return response;
    } catch (error) {
        console.log(error)
        return error
    }
}

```




