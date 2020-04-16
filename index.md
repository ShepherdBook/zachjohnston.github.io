# Hello World

Moved to a [sourcehut wiki](https://man.sr.ht/~zachjohnston/ideas/)

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
