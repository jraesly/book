{% data src="fcq.clean.json" %}
{% enddata %}

# Report

As a class, we brainstormed and came up with a long list of further questions we
can ask based on the FCQ data. Out of these questions, our team chose to tackle on
the following questions. Each member on our team is reponsible for one question.

# How many instructors have taught each subject? Kari

{% lodash %}

var grps = _.groupBy(data, 'Subject')
var ret1 = _.mapValues(grps, function(d){
  var enrollNumbers = _.pluck(d, 'Instructors.name')
  return enrollNumbers.length
  })
return ret1

{% endlodash %}

{{result|json}}

# Does the instruction tends to give out higher grades if they teach more classes? or the reverse? Ming

{% lodash %}
return "[answer]"
{% endlodash %}


# Which department has the lowest enrollment? John

{% lodash %}
var grps = _.groupBy(data, 'CrsPBADept')
var ret1 = _.mapValues(grps, function(d){
  var enrollNumbers = _.pluck(d, 'N.ENROLL')
  return _.sum(enrollNumbers)
  })
  var min = _.min(ret1)
  var dept = _.pick(ret1, function(d){
    return d == min
    })

return dept

{% endlodash %}
<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>


# Which subject is most in demand,based on the total number of enrollment? Sussant

{% lodash %}
return "[answer]"
{% endlodash %}

# Which course has the highest enrollment? Andrew

{% lodash %}
var grps = _.groupBy(data, 'CourseTitle')
var ret1 = _.mapValues(grps, function(d){
  var enrollNumbers = _.pluck(d, 'N.ENROLL')
  return _.sum(enrollNumbers)
  })
  var max = _.max(ret1)
  var bigClass = _.pick(ret1, function(d){
    return d == max
    })

return bigClass

{% endlodash %}

<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>
