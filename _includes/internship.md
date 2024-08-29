<h2 id="internship" style="margin: 2px 0px -15px;">Internship</h2>

<div class="internship">
  <div class="bibliography">

  {% for link in site.data.internship.main %}

  <div class="pub-row">
    <div class="col-sm-3 abbr" style="position: relative; padding-right: 15px; padding-left: 15px;">
      {% if link.image %} 
      <img src="{{ link.image }}" class="teaser img-fluid z-depth-1" style="width: 100%; height: 40%;">
      {% if link.conference_short %} 
      <abbr class="badge">{{ link.conference_short }}</abbr>
      {% endif %}
      {% endif %}
    </div>
    <div class="col-sm-9" style="position: relative; padding-right: 15px; padding-left: 20px;">
      <div class="company"><strong>{{ link.company }}</strong></div>
      <ul>
        <li class="work1">{{ link.work1 }}</li>
        <li class="work2">{{ link.work2 }}</li>
      </ul>
    </div>
  </div>

  {% endfor %}

  </div>
</div>
