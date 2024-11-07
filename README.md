# edu-health

## Instructions

```bash
cd ~
cd ws
rm -rf edu-health #Om den finns
mkdir edu-health && cd edu-health
npm init -y
mkdir src
touch ./src/config.js
touch ./src/server.js
touch ./src/app.js
npm pkg set scripts.start="node ./src/server.js"
npm pkg set scripts.dev="node --watch ./src/server.js"
npm pkg set scripts.test="jest"
npm install express
```

## git

```bash
git init
cat > .gitignore << 'EOF'
node_modules
build
dist
EOF
git add .
git commit -m "Initial commit"

```

## config.js

```bash
cat > ./src/config.js << 'EOF'
const PORT = process.env.PORT || 3000;
module.exports = {PORT}
EOF
```
## server.js

```bash
cat > ./src/server.js << 'EOF'
const {PORT} = require('./config');
const app = require('./app');

const printConfig = () => {
    console.log("Server Configuration:");
    console.log(`- PORT: ${PORT}`);
};

async function startServer() {
    try {
        app.listen(PORT, () => {
            console.log(`Auth Server Listening on ${PORT}`);
            printConfig();
        });
    } catch (err) {
        console.error(`Failed to start the server: ${err}`);
        process.exit(1);
    }
}
startServer();
EOF
```

## app.js

```bash
cat > ./src/app.js << 'EOF'
const express = require('express');
const app = express();
app.use(express.json());


module.exports = app;
EOF
```
