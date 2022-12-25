

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