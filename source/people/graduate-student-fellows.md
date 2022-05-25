---
layout: default
title: NYU DH Graduate Student Fellows
breadcrumbs:
  - name: People
    link: /people
contents_links:
    - label: 'NYU DH Graduate Fellowship Program'
      link: '/funding/grad-fellowships/'
    - label: 'View All Projects'
      link: '/projects'
---
{% assign people = site.data.people | where_exp: "p", "p.site_roles contains 'fellow'" %}
{% assign people = people | sort: 'pid' %}
{% include cards/people.html data=people full_width=false %}
