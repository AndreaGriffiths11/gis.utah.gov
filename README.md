# gis.utah.gov

Read [about our new website](https://gis.utah.gov/about-our-new-v6-website-in-ghpages).
[Contribute](https://gis.utah.gov/about/contributing/) content or typos.
License: [MIT](/LICENSE).

[![Netlify Status](https://api.netlify.com/api/v1/badges/fd943f0d-1816-4377-bdab-866190826309/deploy-status)](https://app.netlify.com/sites/gis-utah-gov/deploys)

## Local Development

1. Check out this repository
1. run `docker-compose up`
1. browse to `localhost:4000`
1. run `docker pull jekyll/jekyll:4` to update your image
1. run `grunt imagemin:images` to minify images

## Common Website Tips

- [Kramdown reference](http://kramdown.gettalong.org/quickref.html)
- [Jekyll Cheat Sheet](http://cheat.jekyll.tips/)

## Markdown syntax conventions

```md
_italics_
**bold**
_**bold italics**_
- list
```

### link to page

- markdown

  ```md
  [link text]({% link path/to/item.with-extension %})
  ```

- html

  ```html
  <a href="{% link path/to/item.with-extension %}">link text</a>
  ```

### link to post

- markdown

  ```md
  [link text]({% link _posts/2016-05-26-file-name.with-extension %})
  ```

- html

  ```html
  <a href="{% link _posts/2016-05-26-file-name.with-extension %}">link text</a>
  ```

### external link

- markdown

  ```md
  [link text](http://external.website.location)
  ```

### images

- markdown

  ```md
  ![alt text]({% link path/to/item.with-extension %})
  ```

- html

  ```html
  <img src="{% link path/to/image.jpg" %} alt="hover text"/>
  ```

### link alt text

```md
[link text]({% link path/to/item.with-extension %} "popup text")
```

### css in markdown

```md
![alt text]({% link path/to/item.with-extension %})
{: .css-class-name}
```

### font matter

- `page` - the post vs page layout
- `title: Title` - the title of the content
- `author.display_name: Full Name` - The author of the content
- `author.email: email@address` - The author email
- `date: 2018-02-13` - the date the content was created
- `update_date: 2018-02-13` - this will show in under the title that the page has been updated
- `tags:` a list of tags
- `categories: Featured|Developer|SGID Blog|GPS-surveyor|Guestblog`
- `published: true|false`

### contact information

Contacts are managed in a [yml file](./_data/contacts.yml). **Please do not put email addresses directly into content**.

The include has a few properties:

- **subject**: the subject of the email link. Most of the time using `page.title` is good enough™
- **contact**: the contact in the yml file to create
- **text**: update this to change the default text generated
- **hide-punctuation**: set this to `true` if you would like to remove the `.` at the end of the text

- markdown

  ```liquid
  {% capture contact %}{% include contact.html subject=page.title contact=site.data.contacts.agrc %}{% endcapture %}
  {{ contact }}
  ```

- html

  ```liquid
  {% include contact.html subject=page.title contact=site.data.contacts.agrc %}
  ```

### hub downloads

This creates the download links from hub.

```yml
Item:
  hub:
    name: ArcGIS Online name exactly eg Utah Address Points
    item_id: the item id
    skip_shapefile: true or false optional
    skip_fgdb: true or false optional
    skip_hub: true or false optional
```
