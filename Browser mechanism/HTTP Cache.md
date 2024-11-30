
## Header key

### Expires

```
Expires: Sat, 30 Nov 2024 12:15:00 GMT
```

如果瀏覽器收到這個 response ，就會把資源快取起來，下次使用者訪問時會檢視該使用者電腦本身的時間是否大於快取時間，如果超過的話就會重新發送請求，否則使用 cache

![[Pasted image 20241130122009.png]]

---

參考來源：

[循序漸進理解 HTTP Cache 機制 · Issue #20 · aszx87410/blog (github.com)](https://github.com/aszx87410/blog/issues/20)