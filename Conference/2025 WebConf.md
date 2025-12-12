# AI 只懂 React？Vue.js 也能 Vibe Coding！- Kuro Hsu

- `<spec>` in SFC

---
# React 優化實戰分析 - 掌握 React 進階技術 x 底層思維


狀態下移：
> state 與 component 放在一起避免 re-reneder

內容上移：
> 透過傳入 children 避免 parent re-render 時也跟著被渲染

 記憶化：
> (1) useMemo 記憶物件，useCallback 記憶 loadUserData
   (2) useEffect 同時包住物件與函數
- 多個 useEffect 用到相同物件或函數
- 將一個參考值，傳遞給子組建時，且用在子組建的依賴陣列裡
- 確定某運算成本高昂
- 子元件被 React.memo 包住時（一個函數作為 props 傳入子組件，若函數沒包 useCallBack 則會被 re-render）
- 每次 re-render 時，物件都會被重新

React.memo
> import { memo } from 'react';
> 搭配 useMemo（值） 或 useCallback（函數） 使用，確保子組件是被記憶化的
>  const MemoParent = memo(Parent)
>  不要直接把物件、陣列、韓式、JSX 寫成 inline-props 

```
<MemoParent>
	<MemoChild>
<MemoParent>

parent 會被 re-render，child 不會
```

Context
> 只要某個組件使用了 context，為 consumer，如果 context 內值改變，consumer 就會被 re-render
> 拆分 provider，把需要記憶化跟不需被記憶化的值分開


```
useReducer
const [state, dispatch] = useReducer(reducer, { isOpen: false });
```


React-compiler
> 沒辦法解決 context 問題


---




