---
layout:     empty
title:      "Find the perfect theme for your Shopify Store"
subtitle:   ""
date:       2015-10-01 12:00:00
author:     "Wolfram Müller"
---
# Find the perfect theme for your Shopify Store
<div>
  <ol id="filters">
    <li data-filter="all">Reset filters</li>
    <li data-filter="free">Free</li>
    <li data-filter="paid">Paid</li>
    <li data-filter="Shopify">Shopify</li>
    <li data-filter="Themeforest">Themeforest</li>
  </ol>
<div>

<div role="main">
  <ul id="themes-container" class="tiles-wrap animated">
    <li data-filter-class='["free", "paid", "Shopify", "Themeforest"]'>
        <a href="https://apps.shopify.com/presskithero" target="_blank">
          <img src="{{ site.baseurl }}/img/themes_screenshots/app.jpg" width="300">
        </a>
        <p>
          <a href="https://apps.shopify.com/presskithero" target="_blank" class="button">Get on Shopify</a>
        </p>
      </li>
    {% for theme in site.data.themes %}
      <li data-filter-class='["{% if theme.price == 'Free' %}free{% else %}paid{% endif %}", "{{theme.store}}"]'>
        <img src="{{ site.baseurl }}/img/themes_screenshots/{{theme.image}}" width="300">
        <p>
          <a href="{{theme.preview_link}}" target="_blank" class="button">Preview</a>
          {{theme.price}} 
          <a href="{{theme.buy_link}}" target="_blank" class="button">Get</a>
        </p>
      </li>
    {% endfor %}
  </ul>
</div>
<script type="text/javascript">
  (function($) {
    $('#themes-container').wookmark();
    var wookmark;
    imagesLoaded('#themes-container', function() {
      wookmark = new Wookmark('#themes-container', {
        fillEmptySpace: true,
        itemWidth: 320,
        offset: 40
      });
    });

    var $filters = $('#filters li');

    function onClickFilter(e) {
      var $item = $(e.currentTarget),
          activeFilters = [],
          filterType = $item.data('filter');
      if (filterType === 'all') {
        $filters.removeClass('active');
      } else {
        $item.toggleClass('active');
        // Collect active filter strings
        $filters.filter('.active').each(function() {
          activeFilters.push($(this).data('filter'));
        });
      }
      wookmark.filter(activeFilters, 'or');
    }
    // Capture filter click events.
    $('#filters').on('click.wookmark-filter', 'li', onClickFilter);
  })(jQuery);
</script>