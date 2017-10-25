+++
# Projects widget.
# This widget displays all projects from `content/course/`.

date = "2016-04-20T00:00:00"
draft = false

title = "Courses"
subtitle = ""
widget = "projects"

# Order that this section will appear in.
weight = 50

# View.
# Customize how projects are displayed.
# Legend: 0 = list, 1 = cards.
view = 1

# Filter toolbar.

# Default filter index (e.g. 0 corresponds to the first `[[filter]]` instance below).
filter_default = 0

# Add or remove as many filters (`[[filter]]` instances) as you like.
# Use "*" tag to show all projects or an existing tag prefixed with "." to filter by specific tag.
# To remove toolbar, delete/comment all instances of `[[filter]]` below.
[[filter]]
  name = "All"
  tag = "*"
  
[[filter]]
  name = "Design and Analysis I"
  course = "ERMA 7300"
  
[[filter]]  
  name = "Design and Analysis II"
  course = "ERMA 7310"
  
[[filter]]
  name = "Design and Analysis III"
  course = "ERMA 8320"

[[filter]]
  name = "Other"
  tag = ".demo"

+++

Courses for which I use this site.