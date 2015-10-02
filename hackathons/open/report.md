{% data src="emergency.json" %}
{% enddata %}

# Report

Use only Javascript and SVG to produce a data analysis / visualization report.

# Authors

This report is prepared by
* [Robbie Kendl](http://github.com/DomoYeti)
* [John Raesly](http://github.com/jraesly)
* [Kevin Gifford](http://github.com/kevinkgifford)

<a name="top"/>
<div id="autonav"></div>

# What borough has the highest number incidents?

{% lodash %}
return _.chain(data)
        .groupBy(function(obj) { return obj["Borough"]; })
        .mapValues(function(arr) { return arr.length; })
        .value();
{% endlodash %}

{{ result | json }}

# Which incident is the most common?
{% lodash %}
return _.chain(data)
        .groupBy(function(obj) { return obj["Incident Type"]; })
        .mapValues(function(arr) { return arr.length; })
        .value();
{% endlodash %}

{{ result | json }}

# Which borough has the highest Fire-1st Alarm incident?

{% lodash %}
var group = _.groupBy(data, "Fire-1st Alarm")
var sum = _.mapValues(group, function(n){
    var fire = _.pluck(n, "Borough")
    return _.sum(fire)
})

return sum

{% endlodash %}

{{result|json}}
