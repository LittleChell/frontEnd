###contents

[&nbsp;&nbsp;&nbsp;&nbsp;detecting css3 feature supporting](#detectCss3Support)

#####<span id="detectCss3Support">detecting css3 feature supporting</span>
>true for supporting, false for the opposite.

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
>

