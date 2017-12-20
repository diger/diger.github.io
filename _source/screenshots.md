---
title: View screnshots
---
<div class="uk-flex uk-flex-around">
  <div class="uk-child-width-1-3@m" uk-lightbox="animation: fade">
    [% USE dir = Directory('screenshots') %]
    [% FOREACH file = dir.files %]
        <a href="screenshots/[% file.name %]" caption="[% file.name.substr(0,-4) %]">
          <img src="screenshots/[% file.name %]" width="500">
        </a>
    [% END %]
  </div>
</div>

