# RemoteAuthToken

Example Repo: [loopback-component-remote-auth-example](https://github.com/mediaburg/loopback-component-remote-auth-example)

### Server Install
```sh
$ cd loopback-auth-server-repo
$ npm install loopback-component-remote-auth --save
```

loopback-auth-server-repo/server/component-config.json
```json
{
...
"loopback-component-remote-auth" : true
...
}
```

loopback-auth-server-repo/server/model-config.js
```js
....
"User": {
    "dataSource": "db",
    "public": true
},
"AccessToken": {
    "dataSource": "db",
    "public": true
},
"ACL": {
    "dataSource": "db",
    "public": true
},
"RoleMapping": {
    "dataSource": "db",
    "public": true
},
"Role": {
    "dataSource": "db",
    "public": true
}
....
```

#### AccessToken

Add to the AccessToken one acl to read the token:

```json
"acls" : [
    .....
    {
      "model" : "AccessToken",
      "property": "findById",
      "accessType": "READ",
      "principalType": "ROLE",
      "principalId": "$owner",
      "permission": "ALLOW"
    }
    .....
]
```



### Client Install

```sh
$ cd loopback-auth-client-repo
$ npm install loopback-component-remote-auth --save
```

loopback-auth-client-repo/server/component-config.json
```json
{
...
"loopback-component-remote-auth" : true
...
}
```

loopback-auth-client-repo/server/model-config.js
```js
....
"AccessToken": {
    "dataSource": "auth-server", // rest to loopback-auth-server-repo
    "public": false
},
"ACL": {
    "dataSource": "auth-server", // rest to loopback-auth-server-repo
    "public": false
},
"RoleMapping": {
    "dataSource": "auth-server", // rest to loopback-auth-server-repo
    "public": false
},
"Role": {
    "dataSource": "auth-server", // rest to loopback-auth-server-repo
    "public": false
},
"User": {
    "dataSource": "auth-server", // rest to loopback-auth-server-repo
    "public": false
}
....
```


License
----

MIT
