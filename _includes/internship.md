<!-- <h2 id="internship" style="margin: 2px 0px -15px;">Internship</h2>

<div class="internship">
  <div class="bibliography">

  {% for link in site.data.internship.main %}

  <div class="pub-row">
    <div class="col-sm-3 abbr" style="position: relative; padding-right: 10px; padding-left: 10px;">
      {% if link.image %} 
      <img src="{{ link.image }}" class="teaser img-fluid z-depth-1" style="width: 100%; height: auto;">
      {% if link.conference_short %} 
      <abbr class="badge">{{ link.conference_short }}</abbr>
      {% endif %}
      {% endif %}
    </div>
    <div class="col-sm-9" style="position: relative; padding-right: 10px; padding-left: 0px;">
      <div class="company" style="margin-left: 0; margin-top: 0;">{{ link.company }}</div>
      <ul style="padding-left: 0; margin-left: 0; margin-top: 5px;">
        <li class="work1" style="margin-left: 0;">{{ link.work1 }}</li>
        <li class="work2" style="margin-left: 0;">{{ link.work2 }}</li>
      </ul>
    </div>
  </div>

  {% endfor %}

  </div>
</div> -->


<h2 id="internship" style="margin: 2px 0px -15px;">Internship</h2>

<div class="publications">
<ol class="bibliography">

{% for link in site.data.internship.main %}

<li>
<div class="pub-row">
  <div class="col-sm-3 abbr" style="position: relative;padding-right: 15px;padding-left: 15px;">
    {% if link.image %} 
    <img src="{{ link.image }}" class="teaser img-fluid z-depth-1" style="width=200;height=40%">
    {% if link.conference_short %} 
    <abbr class="badge">{{ link.conference_short }}</abbr>
    {% endif %}
    {% endif %}
  </div>
  <div class="col-sm-9" style="position: relative;padding-right: 15px;padding-left: 20px;">
      <div class="title">{{ link.company }}</div>
      <div class="author">{{ link.work1 }}</div>
      <div class="author">{{ link.work2 }}</div>
    <div class="links">
      {% if link.pdf %} 
      <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">PDF</a>
      {% endif %}
      {% if link.code %} 
      <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Code</a>
      {% endif %}
      {% if link.page %} 
      <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Project Page</a>
      {% endif %}
      {% if link.bibtex %} 
      <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">BibTex</a>
      {% endif %}
      {% if link.notes %} 
      <strong> <i style="color:#e74d3c">{{ link.notes }}</i></strong>
      {% endif %}
      {% if link.others %} 
      {{ link.others }}
      {% endif %}
    </div>
  </div>
</div>
</li>
<br>

{% endfor %}

</ol>
</div>
