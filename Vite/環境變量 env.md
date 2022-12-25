([环境变量和模式 | Vite 官方中文文档 (vitejs.dev)](https://cn.vitejs.dev/guide/env-and-mode.html#env-files))

---
## 環境變量

### import.meta.env.MODE {string}

> 應用運行的模式，預設模式包含 development, production

#自訂義模式

> 若想要運用不同的模式來 build，可以傳遞 --mode 來覆蓋默認模式
> 並利用 .env.staging 來配置

```
vite build --mode staging
```

---

### import.meta.env.BASE_URL {string}

>合法值
- default:  /
- 絕對路徑： `/foo/`
- 完整 URl： `https://www.google.com/`
- 空字符串或 ： `./`

---
### import.meta.env.PROD {boolean}

> 應用是否運行在生產環境
- 在生產環境中，環境變量會在構建時被靜態替換，
- 所以動態取值是無效的 （`import.meta.env[key]`）

---
### import.meta.env.DEV {boolean}

> 應用是否運行在開發環境（永遠與 `import.meta.env.PROD` 相反）

---
### import.meta.env.SSR {boolean}

> 應用是否運行在 Server 上

---
## .env 文件

```
.env                # 所有情況都會加載
.env.local          # 所有情況都會被加載，但會被 git ignore
.env.[mode]         # 只會在指定模式下加載，比如：`.env.development`
.env.[mode].local   # 只會在指定模式下加載，但會被 git ignore
```

#環境加載優先級
```
- 指定模式的文件，會比通用形式的 `.env` 優先級更高
- Vite 執行時已經存在的環境變量有最高優先級，不會被 `.env` 覆蓋
- .env 類文件會在 Vite 啟動一開始時被加載，改動會在 Server 重啟後生效
```