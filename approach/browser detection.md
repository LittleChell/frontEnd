#	browser detect

Checking the User agent string is not reliable, because it's trivial to spoof this value.

Only use the browser detection method if it's truly necessary, such as showing browser-specific instructions to install an extension. Use feature detection when possible.

##### Opera 8.0+
var isOpera = (!!window.opr && !!opr.addons) || !!window.opera || navigator.userAgent.indexOf(' OPR/') >= 0;

##### Firefox 1.0+
var isFirefox = typeof InstallTrigger !== 'undefined';

##### Safari 3.0+ "[object HTMLElementConstructor]" 
var isSafari = /constructor/i.test(window.HTMLElement) || (function (p) { return p.toString() === "[object SafariRemoteNotification]"; })(!window['safari'] || (typeof safari !== 'undefined' && safari.pushNotification));

##### Internet Explorer 6-11
var isIE = /*@cc_on!@*/false || !!document.documentMode;

##### Edge 20+
var isEdge = !isIE && !!window.StyleMedia;

##### Chrome 1+
var isChrome = !!window.chrome && !!window.chrome.webstore;

##### Blink engine detection
var isBlink = (isChrome || isOpera) && !!window.CSS;


	