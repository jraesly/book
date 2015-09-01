# Analysis

{% import './data.html' as data %}

After completing the warmup exercises, your task is to do four more slightly
more challenges analyses.

## How many students like sushi as their favorite food?

{% lodash %}
var text = _.pluck(data.comments, 'body')
var bodies = _.filter(text, function(str) {
  return str.indexOf('Sushi') > 0
  });
return bodies.length
{% endlodash %}

The answer is {{result}}.

## Who are the students liking Python the most?

{% lodash %}
var text = _.pluck(data.comments, 'body')
var text1 = text.split('Name:')
var body = _.filter(text1, function(py) {
  return py.indexOf('Python') > 0
})
console.log(body)
return body

{% endlodash %}

Their names are {{result}}.

## Are there more Javascript lovers or Java lovers?

{% lodash %}
return "[answer]"
{% endlodash %}

The answer is {{result}}.

## Who like the same food as `kjblakemore`?

{% lodash %}
return "[answer]"
{% endlodash %}

Their names are {{result}}.
