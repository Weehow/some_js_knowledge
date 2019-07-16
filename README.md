# some-js-knowledge  
平时用到的一些js功能整理  
  
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
			
			// 禁止选择文本
			var omitformtags = ["input", "textarea", "select"];
			omitformtagsomitformtags = omitformtags.join("|");
			
			<script type="text/javascript">
				function isIE() {
					if (!!window.ActiveXObject || "ActiveXObject" in window) {
						return true;
					} else {
						return false;
					}
				}

				function resize() {
					var wid = window.innerWidth;
					var realWid = wid < 1440 ? 1440 : wid;
					if (!isIE()) {
						$('.wrap').css('zoom', realWid / 1920)
					}
				}
				resize()
				window.onresize = resize;
			</script>

			function disableselect(e) {
				if (omitformtags.indexOf(e.target.tagName.toLowerCase()) == -1) {
					return false;
				}
			}

			function reEnable() {
				return true;
			}
			if (typeof document.onselectstart != "undefined") {
				document.onselectstart = new Function("return false");
			} else {
				document.onmousedown = disableselect;
				document.onmouseup = reEnable;
			}

