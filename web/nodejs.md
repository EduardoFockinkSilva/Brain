# Node.js

Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine. It allows you to execute JavaScript code server-side.

[Node.js Wikipedia](https://en.wikipedia.org/wiki/Node.js)  
[Node.js Official Website](https://nodejs.org/en)

## Installation

### Using apt (Advanced Packaging Tool)

For Debian-based distributions like Ubuntu, you can use `apt` to install Node.js along with npm (Node.js Package Manager).

```bash
sudo apt update
sudo apt install nodejs npm
```

### Using n

Alternatively, you can use `n` which is a version manager for Node.js.

```bash
sudo npm install -g n
sudo n stable
```


### Version Check

After installation, it's a good idea to check the installed version of Node.js and npm.

\```bash
node -v
npm -v
\```

## Updating Node.js

### Using apt

To update Node.js using `apt`:

\```bash
sudo apt update
sudo apt upgrade nodejs
\```


### Using n

To update Node.js using `n`:

\```bash
sudo n latest
\```



