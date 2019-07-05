# Some-JS-Knowledge  
平时用到的一些JS功能整理  
  
// 禁止右键点击  
document.oncontextmenu = function() {  
  return false;  
}  

if (window.Event) {  
				document.captureEvents(Event.MOUSEUP);  
}

			function nocontextmenu() {
				event.cancelBubble = true
				event.returnValue = false;
				return false;
			}

			function norightclick(e) {
				if (window.Event) {
					if (e.which == 2 || e.which == 3)
						return false;
				} else if (event.button == 2 || event.button == 3) {
					event.cancelBubble = true
					event.returnValue = false;
					return false;
				}
			}
			document.oncontextmenu = nocontextmenu; // for IE5+
			document.onmousedown = norightclick; // for all others
// 禁止Ctrl键  
document.onkeydown = function() {  
  if (event.ctrlKey) return false;  
}  



