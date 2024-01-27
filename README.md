<h1>Ementas de Sistemas Operacionais em Cursos de Ciência da Computação (Bacharelado Presencial) em Universidades Federais do Brasil</h1>

<h3>Objetivo do Repositório:</h3>

<p>Este repositório tem como finalidade reunir as ementas das disciplinas de Sistemas Operacionais presentes nos cursos de Ciência da Computação (Bacharelado Presencial) de diversas Universidades Federais do Brasil. Essas informações serão utilizadas como base para uma pesquisa de final de curso (TCC) que visa elucidar as metodologias, ferramentas e abordagens mais frequentemente adotadas no ensino dessa disciplina.</p>

<h3>Pastas por Universidade:</h3>

<p>Cada universidade terá uma pasta dedicada, identificada pelo seu nome ou abreviação.
Exemplo: UFJ, UFRJ, UFMG, etc.</p>


<h3>Documentos de Ementas:</h3>

<p>Dentro de cada pasta, os documentos de ementas estarão organizados e identificados de acordo com a disciplina.




  <!DOCTYPE html>
<meta charset='utf-8'>
<style> /* CSS styling */

  body {
      font-family: 'Helvetica Neue',Helvetica,Arial,sans-serif;
      font-size: 14px;
  }

  .bar {
    border: 1px solid #0b3536;
    border-radius: 6px;
  }

  #viz .barText {
    fill: #f5faf8;
    font-weight: 500;
  }

  .axisY text, .axisX text, .headerText text{
    fill: #0b3536;
  }

  #viz svg {
    background-color: #f5faf8;
  }

</style>
<head>
  <title>Carga horária dos cursos de Ciência da Computação</title>
</head>
<body>
  <div class='container'>
    <div id='viz'></div>
  </div>
<script src='https://d3js.org/d3.v4.min.js'></script>
<script>

 //Criamos os dados de nosso gráfico
var someData = [ {key: '2011', value: 32},
                 {key: '2012', value: 26},
                 {key: '2013', value: 60},
                 {key: '2014', value: 38},
                 {key: '2015', value: 53},
                 {key: '2016', value: 48},
                 {key: '2017', value: 42},
                 {key: '2018', value: 34},
                 {key: '2019', value: 37},
                 {key: '2020', value: 36},
                {key: 'UFG', value: 33}
];
 
//Retorna todas as keys, como se tivesse feito um loop em um array.
var keys  = someData.map(function(d){ return d.key; });
//Retorna todos os values, como se tivesse feito um loop em um array.  
var values = someData.map(function(d){ return d.value; });

var minValue = d3.min(someData.map(function(d){ return d.value; }));  
var maxValue = d3.max(someData.map(function(d){ return d.value; })); 
var mediumValue = maxValue / 2;
  
var colorBar = d3.scaleLinear()
               .domain([minValue, mediumValue, maxValue])
               .range(["red","yellow","green"])
  
//Aqui só definimos uma margim para o gráfico.
var margin = {top: 50, right: 20, bottom: 30, left: 30},
    width = 760 - margin.left - margin.right,
    height = 380 - margin.top - margin.bottom;

//Criamos a escala maxima para o gráfico, de acordo com a largura/altura
var xScale = d3.scaleBand().rangeRound([0, width]).padding(0.1),
    yScale = d3.scaleLinear().rangeRound([height, 0]);

//Queremos que na xScale contenha as keys
xScale.domain(keys);

//Queremos que na yScale contenha os values de (0 - valorMaximoDoValues)
yScale.domain([0, d3.max(values)]);

// Appending the svg object to the div on the page
var svg = d3.select('#viz').append('svg')
    .attr('width', width + margin.left + margin.right)
    .attr('height', height + margin.top + margin.bottom);

// Appending the 'group' element to the svg
// Moving the 'group' element to the top left margin
var g = svg.append('g')
    .attr('transform', 'translate(' + margin.left + ',' + margin.top + ')');

// Adding header to the chart
g.attr('class', 'headerText')
   .append('text')
   .attr('transform', 'translate(' + (width / 2) + ',' + (-margin.top / 2) + ')')
   .attr('text-anchor', 'middle')
   .attr('font-weight', 600)
   .text('Simple Bar Chart');

// Appending X axis and formatting the text
g.append('g')
    .attr('class', 'axisX')
    .attr('transform', 'translate(0,' + height + ')')
    .call(d3.axisBottom(xScale))
    .attr('font-weight', 'bold');

// Appending Y axis
g.append('g')
    .attr('class', 'axisY')
    .call(d3.axisLeft(yScale).ticks(10));

// Creating chart
var chart = g.selectAll('bar')
    .data(someData)
    .enter().append('g')

// Appending bar chart to the chart
chart.append('rect')
    .attr('class', 'bar')
    .style("fill", function(d){
      return colorBar(d.value);
     })
    .attr('x', function(d) { return xScale(d.key); })
    .attr('height', function(d) { return height - yScale(d.value); })
    .attr('y', function(d) { return yScale(d.value); })
    .attr('width', xScale.bandwidth());

// Appending text to each bar chart
chart.append('text')
    .attr('class', 'barText')
    .attr('x', function(d) { return xScale(d.key); })
    .attr('y', function(d) { return yScale(d.value); })
    .attr('dx', xScale.bandwidth()/2)
    .attr('dy', 20)
    .attr('text-anchor', 'middle')
    .text(function(d){ return d.value + "%"; });

// Adding mouseover and mouseout functions to the chart
chart.on('mouseover', function(d){
      d3.select(this).attr('opacity', 0.7);
      })
    .on('mouseout', function(d){
      d3.select(this)
        .attr('opacity', 1)});

</script>
</body>
Exemplo: Sistemas_Operacionais_UFJ.pdf, SO_UFRJ.docx, etc.</p>

<h3>Formato dos Documentos:</h3>

<ṕ>Os documentos podem estar em PDF, Word, ou outros formatos comuns.
Caso possível, incluir uma cópia da ementa, detalhando conteúdos, metodologias de ensino e formas de avaliação.</p>
