
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

default:  /
> 合法值
> - 絕對路徑： `/foo`

