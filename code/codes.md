####	scrollTop的兼容

`var top = document.documentElement.scrollTop ? document.documentElement.scrollTop : document.body.scrollTop; `

###	css support detected	css属性支持检测
	function detectCSSFeature(featurename){
	    var feature = false,
	    domPrefixes = 'Webkit Moz ms O'.split(' '),
	    elm = document.createElement('div'),
	    featurenameCapital = null;
	
	    featurename = featurename.toLowerCase();
	
	    if( elm.style[featurename] !== undefined ) { feature = true; } 
	
	    if( feature === false ) {
	        featurenameCapital = featurename.charAt(0).toUpperCase() + featurename.substr(1);
	        for( var i = 0; i < domPrefixes.length; i++ ) {
	            if( elm.style[domPrefixes[i] + featurenameCapital ] !== undefined ) {
	              feature = true;
	              break;
	            }
	        }
	    }
	    return feature; 
	}
	}}}