{% vizexercise %}

{% title %}

Add some margins between every two bars

{% data %}

[{name: 'China', pop: 1393783836},
 {name: 'India', pop: 1267401849},
 {name: 'USA', pop: 322583006},
 {name: 'Indonesia', pop: 252812243}]

{% solution %}

var height = 400; // svg window height
var maxPop = _.max(data,function(d){
    return d.pop;
    });
var scale = 400 / maxPop.pop;

function computeX(d, i) {
    return i * 30
}

function computeHeight(d, i, data) {
    var height = 400; // svg window height
    var maxPop = _.max(data,function(d){
        return d.pop;
    });
    var scale = height / maxPop.pop;
    return d.pop * scale;
}

function computeY(d, i) {
    var height = 400; // svg window height
    var maxPop = _.max(data,function(d){
        return d.pop;
    });
    var scale = height / maxPop.pop;
    return height - (d.pop * scale);
}

function computeColor(d, i) {
    return 'red'
}


var viz = _.map(data, function(d, i, data){
            return {
                x: computeX(d, i),
                y: computeY(d, i, data),
                height: computeHeight(d, i, data),
                color: computeColor(d, i)
            }
         })
console.log(viz)

var result = _.map(viz, function(d){
         // invoke the compiled template function on each viz data
         return template({d: d})
     })
return result.join('\n')

{% template %}

<rect x="${d.x}"
      y="${d.y}"
     width="20"
     height="${d.height}"
     style="fill:${d.color};
            stroke-width:3;
            stroke:rgb(0,0,0)" />

{% output %}

<rect x="0"
      y="0"
     width="20"
     height="400"
     style="fill:red;
            stroke-width:3;
            stroke:rgb(0,0,0)" />
<rect x="30"
      y="36.270183004188596"
     width="20"
     height="363.7298169958114"
     style="fill:red;
            stroke-width:3;
            stroke:rgb(0,0,0)" />
<rect x="60"
      y="307.4223713410894"
     width="20"
     height="92.57762865891063"
     style="fill:red;
            stroke-width:3;
            stroke:rgb(0,0,0)" />
<rect x="90"
      y="327.4457813413758"
     width="20"
     height="72.5542186586242"
     style="fill:red;
            stroke-width:3;
            stroke:rgb(0,0,0)" />

{% endvizexercise %}
