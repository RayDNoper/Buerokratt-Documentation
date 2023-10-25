## How to start Bykstack NodeJS docker containers in Inspector mode

### 1. Check the node startup script from package.json. For example, it could be configured as:
```
"scripts": {
	"start": "node server.js"
},
```
or possibly sinply as
```
"main": "server.js",
```

### 2. Copy the projects `docker-compose.yml` to `docker-compose.yml.inspect`

### 3. Add a new entrypoint to your main service:
```
entrypoint: ["node", "--inspect-brk=0.0.0.0:9229", "server.js"]
```

### 4. To expose inspector to the host add this to your main service ports:
```
	ports:
      ...
      - 9229:9229
```

Update the exposed port as necessary.

### 5. Start the inspector in browser:
* for Chomium based browsers go to page chrome://inspect
* for Edge go to edge://inspect

There are other possibilities listed in https://nodejs.org/en/docs/inspector but haven't been tested currently with Bykstack applications.