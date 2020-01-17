## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/authzforce/authzforce.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/authzforce/authzforce.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.


## Generating documentation for PDP configuration XSD 
Install FlexDoc/XML (tested with v1.12.2). 

Install openjfx (e.g. on Ubuntu/Debian):
```
$ sudo apt install openjfx
```

On Linux, modify the JAVA_HOME and CLASS_PATH variables in `.../flexdoc-xml-XXX/bin/linux/generator.sh`:

```
JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
...
# Add JavaFX libraries to the classpath
CLASS_PATH="${FDH}/lib/xml-apis.jar:${FDH}/lib/xercesImpl.jar:${FDH}/lib/resolver.jar:${FDH}/lib/flexdoc-xml.jar:/usr/share/openjfx/lib/*"
```

Run FlexDoc generator from the XSD documentation directory `pdp.xsd/XXX` where `XXX` is the schema version:
```
$ git clone https://github.com/authzforce/authzforce.github.io.git
$ cd authzforce.github.io
$ mkdir -p pdp.xsd/7.1
$ /path/to/flexdoc-xml-XXX/bin/linux/generator.sh
```

In the Generator dialog, and specify:
- Template: `.../flexdoc-xml-XXX/templates/XSDDoc/FramedDoc.tpl`
  - Params: set *Generate Details / For Schemas / Exclude* parameter to `xacml-core-v3-schema-wd-17.xsd;xml.xsd`. OK.
- XML file: `https://raw.githubusercontent.com/authzforce/core/master/pdp-engine/src/main/resources/pdp.xsd`
  - Catalog: add the `catalog.xml`from the [repository](https://github.com/authzforce/authzforce.github.io.git) you just git cloned.
- Output format: HTML

Then hit Run.


