---
title: Dashboard
layout: dashboard
permalink: /dashboard/
---
<h1>Welcome to JKAN's Data Quality Dashboard</h1>

<p>This section of the site is used to manage progress toward Goals and the datasets that factor into acheiving them.</p>

<h2>Goals<h2>
<h3>Subgoals</h3>
<h4>Indicators</h4>
<h5>Datasets</h5>

{% for item in site.data.dashboard.goals %}
{% assign todos = 0 %}
{% assign doings = 0 %}
{% assign dones = 0 %}
{% assign items = 0 %}

{% assign issues_total = 0 %}
{% assign todos_percent = 0 %}
{% assign doings_percent = 0 %}
{% assign dones_percent = 0 %}

    {% for indicator in site.indicators %}
        {% if indicator.goal == item.goal %}
            {% for dataset in indicator.datasets %}
                {% assign datasets = datasets | plus:1 %}
                {% assign todos = todos | plus:dataset.todo %}
                {% assign doings = doings | plus:dataset.doing %}
                {% assign dones = dones | plus:dataset.done %}
            {% endfor %}
        {% endif %}
    {% endfor %}

    {% assign issues_total = todos | plus:doings | plus:dones | round: 1 %}

    {% assign todos_percent = todos | divided_by:issues_total | times:100 %}
    {% assign doings_percent = doings | divided_by:issues_total | times:100 %}
    {% assign dones_percent = dones | divided_by:issues_total | times:100 %}

<div class="media">
  <div class="media-left">
    <a href="{{ item.goal }}_{{ item.short }}">
      <img class="media-object" src="{{ site.baseurl }}/{{ item.icon }}" height="100" width="100" alt="">
    </a>
  </div>
  <div class="media-body">
    <h2>{{ item.short }}</h2>
    {{ item.title }}

    <div class="progress">
      {{ site.data.bootstrap.progress_done }}{{ dones_percent }}{{ site.data.bootstrap.progress_end}}
      {{ site.data.bootstrap.progress_doing }}{{ doings_percent }}{{ site.data.bootstrap.progress_end }}
      {{ site.data.bootstrap.progress_todo }}{{ todos_percent }}{{ site.data.bootstrap.progress_end }}
    </div>
  </div>
</div>
{% endfor %}
