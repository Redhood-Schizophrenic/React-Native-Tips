# React-Native-Tips -> Expo (v.52.0.35 as of now)

<div align="center">
  <p align="center">
      <img src="https://nativewind.dev/img/logo.svg" alt="Tailwind CSS" width="70" height="70">
      <h1 align="center" style="color:red;">NativeWind</h1>
  </p>
</div>
<br />

## Steps to follow 

#### 1. Create a starter code
```bash
  npx create-expo-app@latest
```

#### 2. Reset to blank project
```bash
  npm run reset-project
```

#### 3. Install NativeWind and Supporting Packages
```bash
  npx expo install nativewind tailwindcss react-native-reanimated@3.16.2 react-native-safe-area-context
```

#### 4. Setup Tailwind Config
Run npx tailwindcss init to create a tailwind.config.js file
and Add the paths to all of your component files in your tailwind.config.js file.<br/>
`tailwind.config.js`
```js
  /** @type {import('tailwindcss').Config} */
  module.exports = {
    // NOTE: Update this to include the paths to all of your component files.
    content: ["./app/**/*.{js,jsx,ts,tsx}"],
    presets: [require("nativewind/preset")],
    theme: {
      extend: {},
    },
    plugins: [],
  }
```
#### 5. Setup global.css
Create CSS files with name `global.css` in <b> Root </b> and in <b> app/ </b> directory of project and paste following<br/>
`global.css`
```css
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
```


#### 6. Create Babel and Metro starter configs
Paste this and choose <u><b> babel.config.js, metro.config.js </b></u>
```sh
  npx expo customize
```

#### 7. Add the Babel preset
`babel.config.js`
```js
  module.exports = function (api) {
    api.cache(true);
    return {
      presets: [
        ["babel-preset-expo", { jsxImportSource: "nativewind" }],
        "nativewind/babel",
      ],
    };
  };
```

#### 8. Modify your metro.config.js
`metro.config.js`
```js
  const { getDefaultConfig } = require("expo/metro-config");
  const { withNativeWind } = require('nativewind/metro');
  
  const config = getDefaultConfig(__dirname)
  
  module.exports = withNativeWind(config, { input: './global.css' })
```

#### 8. Modify your metro.config.js
`metro.config.js`
```js
  const { getDefaultConfig } = require("expo/metro-config");
  const { withNativeWind } = require('nativewind/metro');
  
  const config = getDefaultConfig(__dirname)
  
  module.exports = withNativeWind(config, { input: './global.css' })
```

#### 9. Import your CSS file
Insert this into `app/index.tsx` or `app/_layout.tsx`
```js
  import "./global.css"
```

#### 9. Typescript support (optional)
Dont need to do this as the project auto create one if not exists<br/>
`nativewind-env.d.ts`
```js
  /// <reference types="nativewind/types" />
```

### 10. Finally Re-run the code and you're good to go
use --clear as it removes any existing cache and restart it from base
```sh
  npx expo start --clear
```
<br /><br />
## Bye, Have a great time coding.......

<div align="center" >
  <p align="center">
      <img src="https://media.tenor.com/I1Yg9BKSVtkAAAAM/wave-hi.gif" alt="Bye" width="300" height="300">
  </p>
</div>
<br />
