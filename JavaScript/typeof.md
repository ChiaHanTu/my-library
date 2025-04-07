
|**資料型態**|**範例**|typeof **回傳值**|
|---|---|---|
|**Number**|const a = 1;|"number"|
|**String**|const a = "hello";|"string"|
|**Boolean**|const a = true;|"boolean"|
|**Undefined**|let a;|"undefined"|
|**Null**（⚠️ 特例）|const a = null;|"object" 🔥 Bug|
|**Symbol**|const a = Symbol();|"symbol"|
|**BigInt**|const a = 10n;|"bigint"|
|**Object**|const a = { key: "value" };|"object"|
|**Array**（也是 Object）|const a = [1, 2, 3];|"object" 🔥|
|**Function**（唯一的特殊）|function a() {} 或 () => {}|"function"|
|**NaN**（不是型別）|const a = NaN;|"number" ⚠️|
