---
layout: base
title: Download
---

<div id="downloads">
</div>
<script>
$(document).ready(function() {
	$.get("http://dl.symfony2admingenerator.org/",function(data) {
	  	$('#downloads').html(data);
	  });
});
</script>