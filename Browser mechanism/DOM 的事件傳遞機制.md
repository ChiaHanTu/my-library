
![[Pasted image 20241130115956.png]]

1. 點擊 td 元素
2. 點擊事件開始由根節點 window 往下傳到 td  `event.eventPhase === CAPTURING_PHASE`
3. target 的 eventListener 的 eventPhase 就會為 `AT_TARGET`
4. 事件往回傳至根節點，eventPhase 就會為 `BUBBLING_PHASE`




參考來源：

> [DOM 的事件傳遞機制：捕獲與冒泡 (techbridge.cc)](https://blog.techbridge.cc/2017/07/15/javascript-event-propagation/)