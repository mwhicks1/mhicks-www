---
title: Courses
description: |
  This is a list of courses taught, including current and past teaching activities.
author: "The R Markdown Team @RStudio"
show_post_thumbnail: true
show_author_byline: true
show_post_date: true
show_post_time: true
show_button_links: true
# for listing page layout
layout: list # list, list-sidebar

# for list-sidebar layout
sidebar:
  title: Courses
  description: |
    This is a list of courses taught, including current
    and past teaching activities. You can organize them
    by semester, academic year, or course level.

    Check out the _index.md file in the /course folder
    to edit this content.
  author: "The R Markdown Team @RStudio"
  text_link_label: Subscribe via RSS
  text_link_url: /course/index.xml
  show_sidebar_adunit: false # show ad container

# set up common front matter for all pages inside course/
cascade:
  author: "The R Markdown Team @RStudio"
  show_author_byline: true
  show_post_date: true
  show_post_time: true
  show_comments: false # see site config to choose Disqus or Utterances
  # for single-sidebar layout
  sidebar:
    text_link_label: View recent courses
    text_link_url: /course/
    show_sidebar_adunit: false # show ad container
---

** No content below YAML for the course _index. This file provides front matter for the listing page layout and sidebar content. It is also a branch bundle, and all settings under `cascade` provide front matter for all pages inside course/. You may still override any of these by changing them in a page's front matter.**