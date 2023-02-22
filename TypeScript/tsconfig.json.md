``` json
{

  "compilerOptions": {

    "target": "esnext", // 指定編譯生成的 JS 版本

    "module": "esnext",

    "moduleResolution": "node",

    "strict": true,

    "jsx": "preserve",

    "importHelpers": true,

    "experimentalDecorators": true,

    "allowSyntheticDefaultImports": true,

    "sourceMap": true,

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