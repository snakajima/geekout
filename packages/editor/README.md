### Overview

This packages consists of a rich text editor component based on Draft.js and Material UI, and corresponding viewer component. It allows you to store rich text either in Draft.js's raw format or markdown format. 

## MarkdownEditor

This is an WYSIWIG rich text editor component. It takes either raw (Draft.js's raw format) or markdown data as the resource prop (if you give both, it uses raw), and calls back onSave (with markdown and raw), onCancel or onDelete when the user
performs those operations. 

```
  function onSave(markdown, raw) {
    // store either raw or markdown to the database
  }
  const raw = ... // load it from the database
  const resource = { raw }; // or markdown
  return (
    <MarkdownEditor 
      resource={resource} 
      onSave={onSave} 
      onCancel={onCancel} 
      onDelete={onDelete} />
  )
```

## MarkdownViewer

This is a corresponding viewer component, which takes either raw or markdown data as the resource prop. 

```
  return (
    <MarkdownViewer 
      resource={resource} />
  )
```

## raw vs. markdown

The raw format is a Draft.JS specific format, which works really well but not necessarily portable. I recommand to use this format in most of cases. 

The markdown format is a portable format, which is a good format to exchange rich text documents. However, the conversion between raw and markdown is not perfect (it uses draft-js-export-markdown and draft-js-import-markdown), and you may see some unexpected results. 