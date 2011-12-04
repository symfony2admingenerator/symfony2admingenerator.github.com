---
layout: base
title: Download
---

<div id="downloads">
</div>
<script>
$(document).ready(function() {
	$.ajax({
		url: "http://dl.symfony2admingenerator.org/",
		dataType: "jsonp",
		});
});
function content(data) {
	$('#downloads').html(data);
}
</script>