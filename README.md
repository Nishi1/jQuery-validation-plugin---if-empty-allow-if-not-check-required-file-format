# jQuery-validation-plugin- if-empty-allow-if-not-check-required-file-format
jQuery validation plugin - if empty, allow, if not, check required file format


Check the simple code below:

$(function () {	
   
 jQuery(function() {
		jQuery.validator.addMethod("extRegex", function(value, element) {
			ext=(/[.]/.exec(value)) ? /[^.]+$/.exec(value) : undefined;
			var _validFileExtensions = ["jpg", "jpeg", "gif", "png"];
			blnValid=true;
			if(value!=''){
				blnValid=false;
			}
			if (ext!=undefined){
				blnValid=false;
				for (var j = 0; j < _validFileExtensions.length; j++) {
					var sCurExtension = _validFileExtensions[j];					
					if (ext[0].toLowerCase() == sCurExtension.toLowerCase()) {
						blnValid = true;
						break;
					}
				}
			}
			return blnValid
		}, "Only jpg, jpeg, gif and png files allowed.");
 });



	$("Form").validate({	
		rules: {			
			'ImageField' : {
				extRegex: true
			 }
		 }
	});

});


