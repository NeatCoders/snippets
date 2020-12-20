## How to add new...

### Adding a new snippet

You can add a new snippet by simply adding a new post in the `_posts` folder. Jekyll by default forces you to specify a date in the file path: it makes us sad pandas too, but you'll have to stick to this format. You can use dates to control the order in which snippets are displayed in the interface.

Each snippet can define a few values in its YAML header:

Variable | Mandatory | Default | Description
--- | --- | --- | ---
``title`` | Y | - | A short description of what that snippet does.
``path`` | N | - | The URL for the snippet, LEAVE THIS EMPTY
``type`` | N | - | Set it to `JAVA`, `HTML`, `GO`, `JS` or nothing (programming language).

A typical header:

```
---
path: ''
title: 'Delete a thing from string'
type: 'JAVA'

layout: nil
---
```

We then describe the snippet in the body of our post. Check the placeholders present in the `_posts` folder to get an idea of what it can look like.

### Grouping 

Adding a category to your YAML header will allows you to group methods in the navigation. It is particularly helpful as you start having a lot of methods and need to organize them. For example:

```
---
category: Strings
path: ''
title: 'Delete a thing from string'
type: 'JS'

layout: nil
---
```

