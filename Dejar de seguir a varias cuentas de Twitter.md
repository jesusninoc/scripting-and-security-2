# Dejar de seguir a varias cuentas de Twitter
## JavaScript, Web 
### URL: https://www.jesusninoc.com/2016/10/06/dejar-de-seguir-a-varias-cuentas-de-twitter/
```JavaScript
var divs = $('.following .user-actions-follow-button');
var followcounter = 0;
	(function addFollow() {
		setTimeout(function() {
			if (followcounter++ < divs.length) {
				divs[followcounter].clic();
				addFollow();
			}
		}, 4000);	
	})();

```
