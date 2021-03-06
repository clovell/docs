---
Categories: ''
date: 2017-02-22 12:54:02 +0000
description: Allows editors to manage groups of related fields
tags: ''
type: fields
title: Repeatable Field Group Field
image: "/docs/assets/images/Repeatable%20Field%20Group%20Preview.gif"
weight: 12
config:
  code_samples:
    yaml: |
      type: field_group_list
      name: [String]
      label: [String]
      description: [String]
      hidden: [true|false]
      fields: [Array]
      config:
        labelField: [String]
  instructions: |
    The `fields` array accepts the YAML configuration for any field type.
options_image: "/docs/assets/images/Repeatable%20Field%20Group%20Options.jpg"
options:
- name: Hidden
  description: Hides this field in the UI, allowing for hidden default values.
  type: Toggle
- name: Repeatable Field Group Label
  description: Select a text or textarea field to use as the label for each group
  type: Select
how_to_use:
  hugo:
  - code: |
      {{ range .Params.authors }}
      <div class="author">
        <h2>{{ .name }}</h2>
        <small>{{ .bio }}</small>
        <img src="{{ .image }}" alt="Photo of {{ .name }}">
      </div>
      {{ end }}
  jekyll:
  - code: "{% for author in page.authors %}\n<div class=\"author\">\n  <h2>{{ author.name
      }}</h2>\n  <small>{{ author.bio }}</small>\n  <img src=\"{{ author.image }}\"
      alt=\"Photo of {{ author.name }}\">\n</div>\n{% endfor %} \n"
output:
  json: |
    {
      "authors": [
        {
          "name": "Sarah Jane",
          "bio": "Sarah is a writer for the post"
          "image": "/uploads/:year:/:month:/:day:/filename.ext"
        }
      ]
    }
  toml: |
    +++
    [[authors]]
      name = "Sarah Jane"
      bio = "Sarah is a writer for the post"
      image = "/uploads/:year:/:month:/:day:/filename.ext"
    +++
  yaml: "---\nauthors: \n- name: Sarah Jane\n  bio: Sarah is a writer for the post\n
    \ image: /uploads/:year:/:month:/:day:/filename.ext\n---\n"

---
