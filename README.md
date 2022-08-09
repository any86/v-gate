# v-auth

🌱 基于 vue3 + axios + vue-router 实现权限验证.

## 安装

```shell
npm i -S v-auth
```

## 使用
```javascript
// main.js
createAuth({
    router,

    axios: http,

    component404: () => import('@/views/404.vue'),

    async isAuth(to) {
        if (null === permissionRoutes) {
            await http.get('/permission').then(data => {
                permissionRoutes = data.data.routes;
            })
        }
        return permissionRoutes!.some(path => path === to.matched[to.matched.length - 1].path)
    },
});
```