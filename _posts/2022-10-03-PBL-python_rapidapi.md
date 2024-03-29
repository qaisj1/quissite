---
keywords: fastai
description: APIs can be found all over the internet.  A great consolidator of many APIs is <mark>RapidAPI</mark>.  In this blog we will use a site to consolidates API stats.  Learning a few lines of code and you can start extracting lots of data from the internet via APIs.  
title: Python RapidAPI
toc: true
image: /images/rapidapi.png
permalink: /techtalk/rapidapi
categories: [1.A, 5.B, 5.D]
tags: [api, rapidapi]
type: pbl
week: 7
nb_path: _notebooks/2022-10-03-PBL-python_rapidapi.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2022-10-03-PBL-python_rapidapi.ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Python,-RapidAPI-Terms">Python, RapidAPI Terms<a class="anchor-link" href="#Python,-RapidAPI-Terms"> </a></h3><blockquote><p>APIs and tooling like Jupyter docs allows many opportunities in fields like Data Science.  As more and more developers use APIs, they build standards in how you setup a client, send requests and receive information...</p>
</blockquote>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Covid19-RapidAPI-Example">Covid19 RapidAPI Example<a class="anchor-link" href="#Covid19-RapidAPI-Example"> </a></h3><blockquote><p>To begin the API journey.  You need to find an API provider.</p>
</blockquote>
<ul>
<li>RapidAPI is a great option.  You must setup and account, but there are many free options.</li>
<li>Goto this page for starters, the <a href="https://rapidapi.com/spamakashrajtech/api/corona-virus-world-and-india-data/">Corona virus World and India data</a>- Under Code Snippets pick Python - Requests</li>
</ul>
<p>RapidAPI, you will select Python Requests type of code to work with you Notebook.</p>
<ul>
<li>The url is the endpoint to which the API is directed</li>
<li>The headers is a dictionary data structure to send special messaging to the endpoint </li>
<li>The requests.request() python function is used to send a request and retrieve their responses</li>
<li>The response variable receives result of of the request in JSON text</li>
</ul>
<p>Next step, is to format the response according to your data science needs</p>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="sd">&quot;&quot;&quot;</span>
<span class="sd">Requests is a HTTP library for the Python programming language. </span>
<span class="sd">The goal of the project is to make HTTP requests simpler and more human-friendly. </span>
<span class="sd">&quot;&quot;&quot;</span>
<span class="kn">import</span> <span class="nn">requests</span>

<span class="sd">&quot;&quot;&quot;</span>
<span class="sd">RapidAPI is the world&#39;s largest API Marketplace. </span>
<span class="sd">Developers use Rapid API to discover and connect to thousands of APIs. </span>
<span class="sd">&quot;&quot;&quot;</span>
<span class="n">url</span> <span class="o">=</span> <span class="s2">&quot;https://corona-virus-world-and-india-data.p.rapidapi.com/api&quot;</span>
<span class="n">headers</span> <span class="o">=</span> <span class="p">{</span>
    <span class="s1">&#39;x-rapidapi-key&#39;</span><span class="p">:</span> <span class="s2">&quot;98ba704683msh59efed4f43e6ad3p1454bajsn635c4a91117d&quot;</span><span class="p">,</span>
    <span class="s1">&#39;x-rapidapi-host&#39;</span><span class="p">:</span> <span class="s2">&quot;corona-virus-world-and-india-data.p.rapidapi.com&quot;</span>
<span class="p">}</span>

<span class="c1"># Request Covid Data</span>
<span class="n">response</span> <span class="o">=</span> <span class="n">requests</span><span class="o">.</span><span class="n">request</span><span class="p">(</span><span class="s2">&quot;GET&quot;</span><span class="p">,</span> <span class="n">url</span><span class="p">,</span> <span class="n">headers</span><span class="o">=</span><span class="n">headers</span><span class="p">)</span>
<span class="c1"># print(response.text)  # uncomment this line to see raw data</span>

<span class="c1"># This code looks for &quot;world data&quot;</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;World Totals&quot;</span><span class="p">)</span>
<span class="n">world</span> <span class="o">=</span> <span class="n">response</span><span class="o">.</span><span class="n">json</span><span class="p">()</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">&#39;world_total&#39;</span><span class="p">)</span>  <span class="c1"># turn response to json() so we can extract &quot;world_total&quot;</span>
<span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="n">world</span><span class="o">.</span><span class="n">items</span><span class="p">():</span>  <span class="c1"># this finds key, value pairs in country</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">)</span>

<span class="nb">print</span><span class="p">()</span>

<span class="c1"># This code looks for USA in &quot;countries_stats&quot;</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Country Totals&quot;</span><span class="p">)</span>
<span class="n">countries</span> <span class="o">=</span> <span class="n">response</span><span class="o">.</span><span class="n">json</span><span class="p">()</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">&#39;countries_stat&#39;</span><span class="p">)</span>
<span class="k">for</span> <span class="n">country</span> <span class="ow">in</span> <span class="n">countries</span><span class="p">:</span>  <span class="c1"># countries is a list</span>
    <span class="k">if</span> <span class="n">country</span><span class="p">[</span><span class="s2">&quot;country_name&quot;</span><span class="p">]</span> <span class="o">==</span> <span class="s2">&quot;USA&quot;</span><span class="p">:</span>  <span class="c1"># this filters for USA</span>
        <span class="k">for</span> <span class="n">key</span><span class="p">,</span> <span class="n">value</span> <span class="ow">in</span> <span class="n">country</span><span class="o">.</span><span class="n">items</span><span class="p">():</span>  <span class="c1"># this finds key, value pairs in country</span>
            <span class="nb">print</span><span class="p">(</span><span class="n">key</span><span class="p">,</span> <span class="n">value</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>World Totals
total_cases 509,268,964
new_cases 204,268
total_deaths 6,242,509
new_deaths 630
total_recovered 461,827,849
active_cases 41,198,606
serious_critical 42,510
total_cases_per_1m_population 65,334
deaths_per_1m_population 800.9
statistic_taken_at 2022-04-24 11:18:01

Country Totals
country_name USA
cases 82,649,779
deaths 1,018,316
region 
total_recovered 80,434,925
new_deaths 0
new_cases 0
serious_critical 1,465
active_cases 1,196,538
total_cases_per_1m_population 247,080
deaths_per_1m_population 3,044
total_tests 1,000,275,726
tests_per_1m_population 2,990,303
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Digital-Coin-Example">Digital Coin Example<a class="anchor-link" href="#Digital-Coin-Example"> </a></h3><blockquote><p>This example provides digital coin feedback (ie Bitcoin).  It include popularity, price, symbols, etc.</p>
<ul>
<li>A valid X-RapidAPI-Key is required.  Look in code for link to RapidAPI page</li>
<li>Read all comments in code for further guidance</li>
</ul>
</blockquote>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># RapidAPI page https://rapidapi.com/Coinranking/api/coinranking1/</span>

<span class="c1"># Begin Rapid API Code</span>
<span class="kn">import</span> <span class="nn">requests</span>

<span class="n">url</span> <span class="o">=</span> <span class="s2">&quot;https://coinranking1.p.rapidapi.com/coins&quot;</span>
<span class="n">querystring</span> <span class="o">=</span> <span class="p">{</span><span class="s2">&quot;referenceCurrencyUuid&quot;</span><span class="p">:</span><span class="s2">&quot;yhjMzLPhuIDl&quot;</span><span class="p">,</span><span class="s2">&quot;timePeriod&quot;</span><span class="p">:</span><span class="s2">&quot;24h&quot;</span><span class="p">,</span><span class="s2">&quot;tiers[0]&quot;</span><span class="p">:</span><span class="s2">&quot;1&quot;</span><span class="p">,</span><span class="s2">&quot;orderBy&quot;</span><span class="p">:</span><span class="s2">&quot;marketCap&quot;</span><span class="p">,</span><span class="s2">&quot;orderDirection&quot;</span><span class="p">:</span><span class="s2">&quot;desc&quot;</span><span class="p">,</span><span class="s2">&quot;limit&quot;</span><span class="p">:</span><span class="s2">&quot;50&quot;</span><span class="p">,</span><span class="s2">&quot;offset&quot;</span><span class="p">:</span><span class="s2">&quot;0&quot;</span><span class="p">}</span>
<span class="n">headers</span> <span class="o">=</span> <span class="p">{</span>
	<span class="s2">&quot;X-RapidAPI-Key&quot;</span><span class="p">:</span> <span class="s2">&quot;jcmbea0fa2ff5msh7f14bf69be38ca6p175482jsn6c4988114560&quot;</span><span class="p">,</span>  <span class="c1"># place your key here</span>
	<span class="s2">&quot;X-RapidAPI-Host&quot;</span><span class="p">:</span> <span class="s2">&quot;coinranking1.p.rapidapi.com&quot;</span>
<span class="p">}</span>

<span class="n">response</span> <span class="o">=</span> <span class="n">requests</span><span class="o">.</span><span class="n">request</span><span class="p">(</span><span class="s2">&quot;GET&quot;</span><span class="p">,</span> <span class="n">url</span><span class="p">,</span> <span class="n">headers</span><span class="o">=</span><span class="n">headers</span><span class="p">,</span> <span class="n">params</span><span class="o">=</span><span class="n">querystring</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">response</span><span class="o">.</span><span class="n">text</span><span class="p">)</span>
<span class="c1"># End Rapid API Code</span>
<span class="n">json</span> <span class="o">=</span> <span class="n">response</span><span class="o">.</span><span class="n">json</span><span class="p">()</span>  <span class="c1"># convert response to python json object</span>

<span class="c1"># Observe data from an API.  This is how data transports over the internet in a &quot;JSON&quot; text form</span>
<span class="c1"># - The JSON &quot;text&quot; is formed in dictionary {} and list [] divisions</span>
<span class="c1"># - To read the result, Data Scientist of  Developer converts JSON into human readable form</span>
<span class="c1"># - Review the first line, look for the keys --  &quot;status&quot; and &quot;data&quot;</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>{&#34;message&#34;:&#34;You are not subscribed to this API.&#34;}
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Formatting-Digital-Coin-example">Formatting Digital Coin example<a class="anchor-link" href="#Formatting-Digital-Coin-example"> </a></h3><blockquote><p>JSON text transferred from the API in the previous cell was converted to a Python Dictionary called json.  The "coins" in the dictionary contain a list of the most relevant data.   Look at the code and comments to see how the original text is turned into something understandable.   Additionally, there are error check to make sure we are starting the code with the expectation that the API was run correctly.</p>
</blockquote>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="sd">&quot;&quot;&quot;</span>
<span class="sd">This cell is dependent on valid run of API above.</span>
<span class="sd">- try and except code is making sure &quot;json&quot; was properly run above</span>
<span class="sd">- inside second try is code that is used to process Coin API data</span>

<span class="sd">Note.  Run this cell repeatedly to format data without re-activating API</span>
<span class="sd">&quot;&quot;&quot;</span>

<span class="k">try</span><span class="p">:</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;JSON data is Python type: &quot;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">json</span><span class="p">)))</span>
    <span class="k">try</span><span class="p">:</span>
        <span class="c1"># Extracting Coins JSON status, if the API worked</span>
        <span class="n">status</span> <span class="o">=</span> <span class="n">json</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">&#39;status&#39;</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;API status: &quot;</span> <span class="o">+</span> <span class="n">status</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">()</span>
        
        <span class="c1"># Extracting Coins JSON data, data about the coins</span>
        <span class="n">data</span> <span class="o">=</span> <span class="n">json</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">&#39;data&#39;</span><span class="p">)</span>
        
        <span class="c1"># Procedural abstraction of Print code for coins</span>
        <span class="k">def</span> <span class="nf">print_coin</span><span class="p">(</span><span class="n">c</span><span class="p">):</span>
            <span class="nb">print</span><span class="p">(</span><span class="n">c</span><span class="p">[</span><span class="s2">&quot;symbol&quot;</span><span class="p">],</span> <span class="n">c</span><span class="p">[</span><span class="s2">&quot;price&quot;</span><span class="p">])</span>
            <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Icon Url: &quot;</span> <span class="o">+</span> <span class="n">c</span><span class="p">[</span><span class="s2">&quot;iconUrl&quot;</span><span class="p">])</span>
            <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Rank Url: &quot;</span> <span class="o">+</span> <span class="n">c</span><span class="p">[</span><span class="s2">&quot;coinrankingUrl&quot;</span><span class="p">])</span>

        <span class="c1"># Coins data was observed to be a list</span>
        <span class="k">for</span> <span class="n">coin</span> <span class="ow">in</span> <span class="n">data</span><span class="p">[</span><span class="s1">&#39;coins&#39;</span><span class="p">]:</span>
            <span class="n">print_coin</span><span class="p">(</span><span class="n">coin</span><span class="p">)</span>
            <span class="nb">print</span><span class="p">()</span>
            
    <span class="k">except</span><span class="p">:</span>
        <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Did you insert a valid key in X-RapidAPI-Key of API cell above?&quot;</span><span class="p">)</span>
        <span class="nb">print</span><span class="p">(</span><span class="n">json</span><span class="p">)</span>
<span class="k">except</span><span class="p">:</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;This cell is dependent on running API call in cell above!&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>This cell is dependent on running API call in cell above!
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Go-deeper-into-APIs">Go deeper into APIs<a class="anchor-link" href="#Go-deeper-into-APIs"> </a></h3><blockquote><p>Web Development vs Jupyter Notebook.  A notebook is certainly a great place to start.  But, for your end of Trimester project we want you to build the skill to reference and use APIs within your Project.  Here are some resources to get you started with this journey.</p>
</blockquote>
<ul>
<li>In the Nighthawk Coders APCSP you can find an Overview and Examples using APIs:<a href="https://nighthawkcoders.github.io/APCSP/api/overview">APCSP APIs menu</a>- Using Covid RapidAPI<ul>
<li>JavaScript frontend API code in APCSP Fastpages GitHub repo: <a href="https://github.com/nighthawkcoders/APCSP/blob/master/_posts/2022-07-10-PBL-rapidapi.md">https://github.com/nighthawkcoders/APCSP/blob/master/_posts/2022-07-10-PBL-rapidapi.md</a></li>
</ul>
</li>
<li>Making a Jokes API (this will next API tech talk)<ul>
<li>Frontend. JavaScript frontend code in APCSP fastpages GitHub repo: <a href="https://github.com/nighthawkcoders/APCSP/blob/master/_posts/2022-07-10-PBL-jokes.md">https://github.com/nighthawkcoders/APCSP/blob/master/_posts/2022-07-10-PBL-jokes.md</a></li>
<li>Backend Endpoints.  Python code that allows Frontend access: <a href="https://github.com/nighthawkcoders/flask_portfolio/blob/main/api.py">https://github.com/nighthawkcoders/flask_portfolio/blob/main/api.py</a></li>
<li>Backend Jokes Management.  Python code that support Create, Read, Update, Delete (CRUD): <a href="https://github.com/nighthawkcoders/flask_portfolio/blob/main/model_jokes.py">https://github.com/nighthawkcoders/flask_portfolio/blob/main/model_jokes.py</a></li>
</ul>
</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Hacks">Hacks<a class="anchor-link" href="#Hacks"> </a></h2><blockquote><p>Find and use an API as part of your project.  An API and a little coding logic will be a big step toward getting meaningful data for a project.  There are many API providers, find one that might work for your project to complete this hack. When picking an API you are looking for something that will work with either JavaScript Fetch or Python Request.  Here are some samples, these are not qualified in any way.</p>
<ul>
<li><a href="https://rapidapi.com/collection/list-of-free-apis">RapidAPI</a>- <a href="https://github.com/public-apis/public-apis/blob/master/README.md">GitHub Project</a></li>
<li><a href="https://nordicapis.com/9-free-public-apis-that-offer-up-some-cool-open-data/">No Key APIs Article</a></li>
<li><a href="https://developer.twitter.com/en/docs/twitter-api">Twitter Developer</a></li>
<li><a href="https://developers.google.com/apis-explorer">Google Developer</a></li>
<li><a href="https://www.reddit.com/dev/api/">Reddit Developer</a></li>
</ul>
<p>Show API and format results in either Web Page or Jupyter Notebook.  Ultimately, I will expect that we do APIs in backend (Python/Flask).  However, for this Hack you can pick your preference.  We will discuss pros and cons in next API tech talk.</p>
</blockquote>

</div>
</div>
</div>
</div>
 

