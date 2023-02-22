``` json
{

  "compilerOptions": {

    "target": "esnext", // 指定編譯生成的 JS 版本

    "module": "esnext",

    "moduleResolution": "node",

    "strict": true, // 開啟所有 strict family 的設定

    "experimentalDecorators": true, // 支援實驗性修飾器

    "allowSyntheticDefaultImports": true, // 允許自定義載入模組名稱

    "sourceMap": true, 
    // 每次打包時產出 index.js.map ，可以在開發者工具使用原本的 TS 檔案除錯

    "resolveJsonModule": true, // 允許 TS 解析 JSON 檔案，預設無法解析

    "isolatedModules": true,
    // 由於 esbuild 不支援如 const enum 和隱式類型導入，因此必須設為 true

    "esModuleInterop": true, 
    // 解決 TS 將 CommonJS/AMD/USD module 視作 ES6 所產生的規範不符問題

    "lib": ["esnext", "dom"], // 定義瀏覽器規範的型別

    "skipLibCheck": true, // 跳過已知不包含錯誤的聲明檔進行類型檢查（import），縮短編譯時間

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