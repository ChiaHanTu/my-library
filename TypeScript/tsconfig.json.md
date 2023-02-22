``` json
{

  "compilerOptions": {

    "target": "esnext", // 指定編譯生成的 JS 版本

    "module": "esnext",

    "moduleResolution": "node",

    "strict": true, // 開啟所有 strict family 的設定

    "experimentalDecorators": true, // 支援實驗性修飾器

    "allowSyntheticDefaultImports": true, // 允許自定義載入模組名稱

    "sourceMap": true, // 每次打包時產出 index.js.map ，可以在開發者工具使用原本的 TS 檔案除錯

    "resolveJsonModule": true,

    "isolatedModules": true,

    "esModuleInterop": true,

    "lib": ["esnext", "dom"],

    "skipLibCheck": true,

    "types": [

      "node",

      "vite/client",

      "element-plus/global"

    ],

    "baseUrl": ".",

    "paths": {

      "@/*": ["src/*"]

    }

  },

  "include": ["src/**/*.ts", "src/**/*.d.ts", "src/**/*.tsx", "src/**/*.vue", "types/**/*.d.ts", "vite.config.ts"],

  "exclude": ["node_modules", "dist"]

}
```