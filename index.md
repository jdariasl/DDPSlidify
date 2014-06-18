---
title       : Introduction to Kernel Non-Parametric Estimation of Statistical Models
subtitle    : 
author      : Julián D. Arias Londoño
job         : Coursera course - Developing Data Products 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax, bootstrap, quiz, shiny, interactive]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
ext_widgets: {rCharts: [libraries/nvd3]}

--- .class #id 

## Introduction to Non-Parametric Statistical Models

Statistical models are very useful tools in several fields of Engineering and Sciences. Perhaps two of the most commonly used statistical models are: 

<ul>
<li>Multiple Linear Regression or</li>
<li>Multivariate Gaussian Density function based on the Maximum Likelihood criterion. </li>
</ul> 


One of the main drawbacks of these kind of models is the implicit assumption about the nature of the data. <b> Non-parametrics (NP) models </b>, are a class of data-driven statistical models that can be build without making assumptions about the data structure. 

In the following slides, the application of NP models is shown in three different context: 

<ul>
<li>Probability Density Estimation</li>
<li>Regression </li>
<li>Classification </li>
</ul> 

--- .class #id 

## Probabilistic Density Functions

<font size="2"> The most used NP density estimator is the Histogram, which provides a hard estimation of a density function. There exist another kind of NP estimators that can provide smooth estimations in the same context. One of them is the <b>Parzen Window</b> or <b>Kernel</b> estimator. Given a set of samples $\left\lbrace {\bf{x}}_j\right\rbrace _{j=1}^N$, the kernel density estimator is given by: $p({\bf{x}}^*) = \frac{1}{Nh}\sum_{j=1}^N K(({\bf{x}}_j - {\bf{x}}^*)/h)$, where $K(\cdot)$ is the kernel function and $h$ is the bandwidth. </font> 

<div class="row-fluid">
  <div class="span4">
    <form class="well">
      <div>
        <label class="control-label" for="n">
          <h4>Number of samples</h4>
        </label>
        <input id="n" type="slider" name="n" value="100" class="jslider" data-from="10" data-to="200" data-step="1" data-skin="plastic" data-round="FALSE" data-locale="us" data-format="#,##0.#####" data-smooth="FALSE"/>
      </div>
      <div>
        <label class="control-label" for="h">
          <h4>Bandwidth Kernel estimatior</h4>
        </label>
        <input id="h" type="slider" name="h" value="0.5" class="jslider" data-from="0.01" data-to="2" data-step="0.00796" data-skin="plastic" data-round="FALSE" data-locale="us" data-format="#,##0.#####" data-smooth="FALSE"/>
      </div>
    </form>
  </div>
  <div class="span8">
    <div class="tabbable tabs-above">
      <ul class="nav nav-tabs">
        <li class="active">
          <a href="#tab-6414-1" data-toggle="tab">Histogram</a>
        </li>
        <li>
          <a href="#tab-6414-2" data-toggle="tab">Kernel function</a>
        </li>
      </ul>
      <div class="tab-content">
        <div class="tab-pane active" height="200px" width="400px" id="tab-6414-1">
          <div id="distPlot" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
        </div>
        <div class="tab-pane" id="tab-6414-2">The kernel function used is: Radial Basis Function</div>
      </div>
    </div>
  </div>
</div>


--- .class #id 

## Kernel Regression

<font size="4"> In the same way as before, we can use NP estimators for regression problems. For the sake of comparison, here we are going to use the Nadaraya-Watson kernel regression and a k-Nearest Neighbor estimation.  </font> 

<div class="row-fluid">
  <div class="span4">
    <form class="well">
      <div>
        <label class="control-label" for="n2">
          <h4>Number of samples</h4>
        </label>
        <input id="n2" type="slider" name="n2" value="100" class="jslider" data-from="10" data-to="200" data-step="1" data-skin="plastic" data-round="FALSE" data-locale="us" data-format="#,##0.#####" data-smooth="FALSE"/>
      </div>
      <div>
        <label class="control-label" for="h2">
          <h4>Bandwidth Kernel estimatior</h4>
        </label>
        <input id="h2" type="slider" name="h2" value="0.5" class="jslider" data-from="0.01" data-to="2" data-step="0.00796" data-skin="plastic" data-round="FALSE" data-locale="us" data-format="#,##0.#####" data-smooth="FALSE"/>
      </div>
      <div>
        <label class="control-label" for="k">
          <h4>Number of Nearest Neighbors</h4>
        </label>
        <input id="k" type="slider" name="k" value="5" class="jslider" data-from="1" data-to="20" data-step="1" data-skin="plastic" data-round="FALSE" data-locale="us" data-format="#,##0.#####" data-scale="|;|;|;|;|;|;|;|;|;|;|;|;|;|;|;|;|;|;|;|" data-smooth="FALSE"/>
      </div>
    </form>
  </div>
  <div class="span8">
    <div class="tabbable tabs-above">
      <ul class="nav nav-tabs">
        <li class="active">
          <a href="#tab-1052-1" data-toggle="tab">Kernel Regressor</a>
        </li>
        <li>
          <a href="#tab-1052-2" data-toggle="tab">K-NN Regressor</a>
        </li>
      </ul>
      <div class="tab-content">
        <div class="tab-pane active" id="tab-1052-1">
          <div id="distPlot2" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
        </div>
        <div class="tab-pane" id="tab-1052-2">
          <div id="distPlot3" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
        </div>
      </div>
    </div>
  </div>
</div>

--- .class #id 

## Kernel Decision boundary

<div class="row-fluid">
  <div class="span4">
    <form class="well">
      <label class="control-label" for="Features">Choose Features</label>
      <select id="Features"><option value="SepalLength~SepalWidth" selected>SepalLength~SepalWidth</option>
<option value="SepalLength~PetalWidth">SepalLength~PetalWidth</option>
<option value="SepalLength~PetalLength">SepalLength~PetalLength</option>
<option value="PetalLength~PetalWidth">PetalLength~PetalWidth</option>
<option value="SepalWidth~PetalLength">SepalWidth~PetalLength</option>
<option value="SepalWidth~PetalWidth">SepalWidth~PetalWidth</option></select>
      <script type="application/json" data-for="Features" data-nonempty="">{}</script>
      <div>
        <label class="control-label" for="h3">
          <h4>Bandwidth Kernel estimatior</h4>
        </label>
        <input id="h3" type="slider" name="h3" value="0.5" class="jslider" data-from="0.01" data-to="2" data-step="0.00796" data-skin="plastic" data-round="FALSE" data-locale="us" data-format="#,##0.#####" data-smooth="FALSE"/>
      </div>
    </form>
  </div>
  <div class="span8">
    <div class="tabbable tabs-above">
      <ul class="nav nav-tabs">
        <li class="active">
          <a href="#tab-1241-1" data-toggle="tab">Scatter Plot</a>
        </li>
        <li>
          <a href="#tab-1241-2" data-toggle="tab">Decision Boundary</a>
        </li>
      </ul>
      <div class="tab-content">
        <div class="tab-pane active" id="tab-1241-1">
          <div id="chart2" class="shiny-html-output nvd3 rChart"></div>
        </div>
        <div class="tab-pane" id="tab-1241-2">
          <div id="distPlot5" class="shiny-plot-output" style="width: 100% ; height: 400px"></div>
        </div>
      </div>
    </div>
  </div>
</div>
