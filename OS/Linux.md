
### Chmod 命令

> 為 change mode 縮寫，控制系統用戶對文件的權限的命令

 | User(U) | Group(G) | Other Users(O) | All(A) |
 | ------- | -------- | -------------- | ------ |
 | rwx     | rx       | r              |        |
 | 7       | 5        | 4              |        |

- r: Read 讀取，代表數字 4 
- w: Write 寫入，代表數字 2
- x: Execute 執行，代表數字 1

```

```權限數字代表的為各個權限的總和
ex: 
7: 4 + 2 + 1
5: 4 + 1

