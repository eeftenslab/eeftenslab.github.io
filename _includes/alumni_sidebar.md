## Lab Alumni
{% assign sorted = (site.members | sort: "enddate") | reverse %}
{% for member in sorted %}

{% if member.enddate == empty %}
{% continue %}
{% endif %}

{% assign position = member.position | downcase %}
{% if position contains "srtp" or position contains "intern" or position contains "sep" or position contains "visiting" %}
{% continue %}
{% endif %}

<hr>
<div id = "{{member.name}}" style="padding-top: 60px; margin-top: -60px;">
<p><strong>{{member.name}}</strong> - <em>{{member.position | markdownify | remove: '<p>' | remove: '</p>' }}</em><br>



{% assign start = member.startdate | first | date:"%Y" %}
{% assign end = member.enddate | last | date:"%Y" %}


{% if start == end %}
{{ start }}<br>
{% else %}
{{ start }} - {{ end }}<br>
{% endif %}

{% if member.subsequent %}
Subsequently: {{member.subsequent}} <br>
{% endif %}

{% if member.email %}
{% unless member.email contains "ucsf.edu" or "fr" %}
<em>{{member.email}}</em> <br>
{% endunless %}
{% endif %}

{% if member.website %}
<a style="overflow-wrap: break-word;" href= "{{member.website}}">{{member.website}}</a> <br>
{% endif %}

{% if member.orcid %}
<a href="http://orcid.org"><img class="inline-block mem-icon" src="/static/img/logo/orcid_logo.svg"></a>
<a href="http://orcid.org/{{member.orcid}}"> {{member.orcid}}</a> <br>
{% endif %}

{% if member.linkedin %}
<a href="http://www.linkedin.com"><img class="inline-block mem-icon" src="/static/img/logo/linkedin_logo.svg"></a>
<a href= "http://www.linkedin.com/in/{{member.linkedin}}"> {{member.linkedin}} </a> <br>
{% endif %}

{% if member.scholar %}
<a href="http://scholar.google.com"><img class="inline-block mem-icon" src="/static/img/logo/gscholar_logo.svg"></a>
<a href= "http://scholar.google.com/citations?user={{member.scholar}}"> Scholar Citations </a> <br>
{% endif %}

{% if member.twitter %}
<a href="http://twitter.com"><img class="inline-block mem-icon" src="/static/img/logo/twitter_logo.svg"></a>
<a href= "http://twitter.com/{{member.twitter}}"> @{{member.twitter}} </a> <br>
{% endif %}

{% if member.github %}
<a href="http://github.com"><img class="inline-bloc mem-icon" src="/static/img/logo/github_logo.svg"></a>
<a href= "http://github.com/{{member.github}}"> {{member.github}} </a> <br>
{% endif %}
</p>
</div>
{% endfor %}
