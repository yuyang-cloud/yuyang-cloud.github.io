# <i class="fas fa-file-alt"></i> Publications

<div class="publication-filter" aria-label="Publication categories">
  <button class="publication-filter-btn active" type="button" data-publication-filter="all">All</button>
  <button class="publication-filter-btn" type="button" data-publication-filter="agent">Agent</button>
  <button class="publication-filter-btn" type="button" data-publication-filter="world-model">World Model</button>
  <button class="publication-filter-btn" type="button" data-publication-filter="vision-3d">3D Vision</button>
</div>

{% for link in site.data.publications.main %}
{% assign publication_categories = link.categories | default: empty | join: ' ' %}
<div class='paper-box floating-card{% if link.hide_by_default %} publication-hidden{% endif %}' data-publication-categories="{{ publication_categories }}" data-publication-default-hidden="{{ link.hide_by_default | default: false }}">
  <div class='paper-box-image'>
    {% if link.image %}
    <img src='{{ link.image }}' alt="{{ link.title }}" width="100%">
    {% endif %}
  </div>
  <div class='paper-box-text'>
    <h3 class="publication-title">
      {% if link.page %}
      <a href="{{ link.page }}" style="color: inherit; text-decoration: none;">{{ link.title }}</a>
      {% elsif link.pdf %}
      <a href="{{ link.pdf }}" style="color: inherit; text-decoration: none;">{{ link.title }}</a>
      {% else %}
      {{ link.title }}
      {% endif %}
    </h3>
    <div class="authors">{{ link.authors }}</div>
    <div class="venue"><em>{{ link.conference }}</em></div>
    {% if link.venue_label or link.conference_short or link.workshop %}
    {% assign label_text = link.venue_label | default: link.conference_short %}
    {% assign label_lower = label_text | downcase %}
    <div class="publication-labels">
      {% if link.venue_label or link.conference_short %}
      <span class="publication-label">
        {% if label_lower contains '(oral)' %}
        {{ label_text | replace: ' (Oral)', '' | replace: '(Oral)', '' | replace: ' (oral)', '' | replace: '(oral)', '' | strip }} <span class="publication-label-oral">(Oral)</span>
        {% else %}
        {{ label_text }}
        {% endif %}
      </span>
      {% endif %}
      {% if link.workshop %}
      <span class="publication-label publication-label-workshop">{{ link.workshop }}</span>
      {% endif %}
    </div>
    {% endif %}
    <div class="links">
      {% if link.pdf %}
      <a href="{{ link.pdf }}" class="btn-accent"><i class="fas fa-file-alt"></i> Paper</a>
      {% endif %}
      {% if link.page %}
      <a href="{{ link.page }}" class="btn-accent"><i class="fas fa-home"></i> Project</a>
      {% endif %}
      {% if link.code %}
      <a href="{{ link.code }}" class="btn-accent"><i class="fab fa-github"></i> Code</a>
      {% endif %}
      {% if link.repo %}
      <a href="{{ link.repo }}" class="btn-accent"><i class="fab fa-github"></i> Repo</a>
      {% endif %}
      {% if link.model %}
      <a href="{{ link.model }}" class="btn-accent"><i class="fas fa-cube"></i> Model</a>
      {% endif %}
      {% if link.data %}
      <a href="{{ link.data }}" class="btn-accent"><i class="fas fa-database"></i> Dataset</a>
      {% endif %}
      {% if link.bibtex %}
      <a href="{{ link.bibtex }}" class="btn-accent"><i class="fas fa-quote-right"></i> BibTeX</a>
      {% endif %}
    </div>
  </div>
</div>
{% endfor %}

<script>
document.addEventListener('DOMContentLoaded', function() {
  const filterButtons = document.querySelectorAll('.publication-filter-btn');
  const publicationItems = document.querySelectorAll('.paper-box[data-publication-categories]');

  function applyPublicationFilter(selectedCategory) {
    publicationItems.forEach(item => {
      const categories = (item.dataset.publicationCategories || '').split(/\s+/);
      const hiddenByDefault = item.dataset.publicationDefaultHidden === 'true';
      const shouldShow = selectedCategory === 'all' ? !hiddenByDefault : categories.includes(selectedCategory);
      item.classList.toggle('publication-hidden', !shouldShow);
    });
  }

  filterButtons.forEach(button => {
    button.addEventListener('click', function() {
      const selectedCategory = button.dataset.publicationFilter;

      filterButtons.forEach(item => {
        item.classList.toggle('active', item === button);
      });

      applyPublicationFilter(selectedCategory);
    });
  });

  applyPublicationFilter('all');
});
</script>
