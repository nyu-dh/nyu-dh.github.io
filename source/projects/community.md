---
title: NYU Community DH Projects
subtitle: ''
layout: default
breadcrumbs:
  - name: Projects
    link: /projects
---
{% assign projects = site.projects | where_exp: "i", "i.category contains 'Other'" %}
{% include cards/projects.html data=projects full_width=false %}
