---
layout: page
title: Search Results
footer: false
---

{% include custom/lunr-search/entries.html %}
<script type="text/javascript">
 loadScript("{{ root_url }}/javascripts/lunr_search.js", function() {
   $(document).ready(function() {
     return new LunrSearch(
       "#search-query",
       {
         indexUrl:"/search.json",
         results:"#search-results",
         entries:".entries",
         template:"#search-results-template"
       }
     )
   })
 }, true);
</script>


