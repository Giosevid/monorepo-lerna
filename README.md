# monorepo-lerna

## Installation

```bash
npm i lerna@2.0.0-beta.20 -g
mkdir my-monorepo && cd $_ && lerna init
```

```bash
cd packages
mkdir alpha
cd alpha
npm init -y
echo "module.exports = 'alpha'" > index.js
```

```bash
cd ..
```

```bash
mkdir beta
cd beta
npm init -y
echo "module.exports = 'beta'" > index.js
```

```bash
cd ..
```

```bash
mkdir usage
cd usage
npm init -y
touch index.js
```

```bash
Open up /packages/usage/index.js in a text editor and paste this in.
var alpha = require('alpha')
var beta = require('beta')
console.log(alpha + " " + beta)
```

What you want to do now is go into /packages/usage/package.json and add these lines under dependencies.
```json
{
  "dependencies": {
    "alpha": "1.0.0",
    "beta": "1.0.0"  
  }
}
```

```bash
lerna bootstrap
```

```bash
brew install tree
```

```bash
├── README.md
├── lerna.json
├── package.json
└── packages
    ├── alpha
    │   ├── index.js
    │   ├── node_modules
    │   └── package.json
    ├── beta
    │   ├── index.js
    │   ├── node_modules
    │   └── package.json
    └── usage
        ├── index.js
        ├── node_modules
        │   ├── alpha
        │   │   ├── index.js
        │   │   └── package.json
        │   └── beta
        │       ├── index.js
        │       └── package.json
        └── package.json
```

```bash
node ./packages/usage/index.js
```

## output
alpha beta