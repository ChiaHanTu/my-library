
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
權限數字代表的為各個權限的總和
ex: 
	7: 4 + 2 + 1
	5: 4 + 1
```

### 八進制語法

| #   | 權限           | rwx | 二進制 |
| --- | -------------- | --- | ------ |
| 7   | 讀 + 寫 + 執行 | rwx | 111    |
| 6   | 讀 + 寫        | rw- | 110    |
| 5   | 讀 + 執行      | r-x | 101    |
| 4   | 讀             | r-- | 100    |
| 3   | 寫 + 執行      | -wx | 011    |
| 2   | 寫             | -w- | 010    |
| 1   | 執行           | --x | 001    |
| 0   | 無             | --- | 000    |

## 命令 

```
chmod [-cfvR] [--help] [--version] mode file...
```

ex:

```
chmod ugo+r file1.txt // 將所有人添加讀取權限


```

### 參考來源：

- https://www.runoob.com/linux/linux-comm-chmod.html