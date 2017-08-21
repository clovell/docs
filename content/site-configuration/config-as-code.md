---
Categories: []
date: 2017-08-20T15:25:43+00:00
description: "Allows configuration of Forestry in your site’s source code"
tags: []
title: Config as Code
---
Forestry stores the settings and configuration of the CMS for each site in a `.forestrio/` folder in your site’s source code. This allows developers to create default configurations that can be shared between multiple sites, and to deliver source code with Forestry CMS pre-configured.

When importing a new site, a `.forestryio/` folder will be added to your site’s source. Any changes made to your CMS’ configuration will be committed to your site’s sourcein this folder.

## Site Settings
Your site settings are configured from `.forestryio/settings.yml`.

The following is an example of `settings.yml` for a Hugo site.

```
---
upload_path: "/static/uploads/:year:/:month:/:day:"
frontmatter_file_url_template: "/uploads/:year:/:month:/:day:"
body_file_url_template: "/uploads/:year:/:month:/:day:"
new_page_extension: md
auto_deploy: false
admin_path: "/admin"
webhook_url: http://example.com/webhook
sections:
  posts:
    default_front_matter_template: posts
  pages:
    default_front_matter_template: pages
version: 0.26
---
```

### Options

**Admin Path** `admin_path:` `string`

Allows you to configure the path where the Remote Admin will be deployed.

---

**Upload Path** `upload_path:` `string`

Allows you to configure the path where media assets are uploaded

---

**Front Matter File URL Template** `frontmatter_file_url_template:` `string`

Allows you to configure the path that is set when adding images to Front Matter Fields. *Note: this value is set at upload time.*

---

**Body File URL Template** `body_file_url_template: ` `string`

Allows you to configure the path that is used when adding images to the body of a page. *Note: this value is set at upload time.*

---

**New Page Extension** `new_page_extension:` `md|html`

Allows you to configure whether new pages are created as `.md` or `.html` files.

---

**Auto Deploy** `auto_deploy:` `boolean`

Allows you to configure if publishing should be trigged when a commit is made to the source repository.

---

**Webhook URL** `webhook_url` `string`

Allows you to provide a [web hook](/site-configuration/web-hooks/) to be trigged when events occur in Forestry.

---

**Sections** *(Hugo-only)* `sections` `object` 

Allows you to configure the default Front Matter Template for content in each section.

Sections are mapped by their directory structure inside the `/content` folder.

The options available for each section is:

**Default Front Matter Template** `default_front_matter_template` `string`

The Front Matter Template applied to any pages without a Front Matter Template. Set the value to the file name of the Front Matter Template without the file extension, or `none` to remove the current template from the section.

Example:
````
sections:
  posts:
    default_front_matter_template: example-template
````

---

**Collections** *(Jekyll-only)* `sections` `object` 

Allows you to configure the default Front Matter Template for content in each collection.

Collections are mapped by their directory structure inside the root of your Jekyll site.

The options available for each collection is:

**Default Front Matter Template** `default_front_matter_template` `string`

The Front Matter Template applied to any pages without a Front Matter Template. Set the value to the file name of the Front Matter Template without the file extension, or `none` to remove the current template from the section.  Example:

````
collections:
  _posts:
    default_front_matter_template: posts
````

---

**Version** *(Hugo-only)* `version:` `string` 
This allows you to configure the version of Hugo your site uses. This is limited to the latest versions of Hugo [supported by Forestry](https://forestry.io/docs/faq/what-versions-of-hugo-do-you-support/).

## Front Matter Templates
The configuration files for Front Matter Templates is found in `.forestryio/front_matter/templates/`. Each Front Matter Template is stored as a separate file.

When importing a site for the first time in Forestry, these configuration files will take precedence over autogeneration from any Jekyll defaults or Hugo archetypes.

The following is an example of a front matter template configuration file.

```
homepage.yml
---
pages:
- index.md
hide_body: false
fields:
- name: title
  default: ''
  label: Title
  hidden: false
  type: text
- name: publishDate
  default: ''
  label: Date
  hidden: false
  type: datetime
- name: Categories
  default: []
  label: Categories
  hidden: false
  type: list
---
```



### Options

**Pages** `pages:` `array`

Provide an array of relative page paths that you want the front matter template to apply to.

For Jekyll, provide the relative path from the project root, e.g, `_posts/2017-01-01-example.md`.

For Hugo, provide the relative path from your content directory, e.g, `posts/2017-01-01-example.md`.

*Note: if a page is defined in multiple Front Matter Templates, the last Front Matter Template in alphanumerically order will be applied.*

---

**Hide Body** `hide_body:` `boolean`

Toggle the display of the body editor on or off for this Front Matter Template.

---

**Fields** `fields:` `array`

The array of fields in this front matter template. They follow a standard format:

- `type` `string` The field type.
- `name` `string` The name or key of the field
- `label` `string` The label displayed in the CMS interface
- `description` `string` Help text that appears above the field 
- `hidden` `boolean` Toggle display of the field in the interface on or off
- `config` `object` Field-specific configuration options
- `fields` `array` An array of fields. For field groups and repeatable field groups only.

For a comprehensive overview of field configuration, see the [field type documentation](/docs/site-configuration/front-matter-fields#field-types).

### Removing & Renaming Files

To prevent the accidental deletion of Front Matter Templates, Front Matter Templates **must** be removed using the interface in the CMS.

To prevent accidental deletion, any configuration files removed from the repo will remain in the CMS and be re-added to your site’s source on the next save or publish unless removed in Forestry. 

Renaming configuration files is treated as the creation of a new Front Matter Template. In this scenario, both the original and new templates will exist in the CMS, and the original will be re-added to your site’s source on the next save or publish unless removed in Forestry.

