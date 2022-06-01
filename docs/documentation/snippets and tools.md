---
share: true
---

I, as working on my blog, created some cool snippets or useful tools.

# Grid CSS snippets

Automatically convert the [grid callout layout (from ITS)](https://github.com/SlRvb/Obsidian--ITS-Theme/blob/main/S%20-%20Callouts.css) to mkdocs

![[example_grid_layout.png]]

Add this to [`custom_attribute.css`](https://github.com/Mara-Li/obsidian-mkdocs-publisher-template/blob/main/docs/assets/css/custom_attributes.css)

```css
:root {
    --md-admonition-icon--grid: url('data:image/svg+xml;charset=utf-8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512"><path d="M352 432c0 8.836-7.164 16-16 16H176c-8.838 0-16-7.164-16-16V128H48c-26.51 0-48 21.5-48 48v288c0 26.51 21.49 48 48 48h416c26.51 0 48-21.49 48-48v-80H352v48zm-248 7c0 4.969-4.031 9-9 9H65c-4.969 0-9-4.031-9-9v-30c0-4.969 4.031-9 9-9h30c4.969 0 9 4.031 9 9v30zm0-104c0 4.969-4.031 9-9 9H65c-4.969 0-9-4.031-9-9v-30c0-4.969 4.031-9 9-9h30c4.969 0 9 4.031 9 9v30zm0-104c0 4.969-4.031 9-9 9H65c-4.969 0-9-4.031-9-9v-30c0-5 4.03-9 9-9h30c4.969 0 9 4.031 9 9v30zm304 178c0-4.969 4.031-9 9-9h30c4.969 0 9 4.031 9 9v30c0 4.969-4.031 9-9 9h-30c-4.969 0-9-4.031-9-9v-30zM591.1 0h-352c-25.6 0-48 21.49-48 48v256c0 26.51 21.49 48 48 48h352c26.51 0 48-21.49 48-48V48c.9-26.51-20.6-48-48-48zm-288 64c17.68 0 32 14.33 32 32s-14.32 32-32 32c-16.8 0-32-14.3-32-32s15.2-32 32-32zm271 215.6c-2.8 5.2-8.2 8.4-14.1 8.4H271.1c-6 0-10.6-3.4-13.4-8.7-2.7-5.4-2.2-11.9 1.4-16.7l70-96c3-4.2 7.8-6.6 12-6.6 5.11 0 9.914 2.441 12.93 6.574l22.35 30.66 62.74-94.11C442.1 98.67 447.1 96 453.3 96c5.348 0 10.34 2.672 13.31 7.125l106.7 160c3.29 4.875 3.59 11.175.79 16.475z"/></svg>');
}

.md-typeset .admonition.grid {
    box-shadow: none;
}

.md-typeset .admonition.grid p:not(.admonition-title) {
    display: flex;
    margin-block-start: 0;
    margin-block-end: 0;
    justify-content: center;
}

.md-typeset .admonition.grid img {
    display: table-cell;
    vertical-align: middle;
    padding: 1px;
    width: 75%;
    height: 75%;
}
```

# Add a image banner to mkdocs

![image](https://user-images.githubusercontent.com/30244939/163732766-d08b102f-508b-496e-a99f-68f865b2080b.png)

You can add a cool image banner with editing [`utils.css`](https://github.com/Mara-Li/obsidian-mkdocs-publisher-template/blob/main/docs/assets/css/utils.css) and adding :
```css
.md-header {
    background: var(--md-primary-fg-color) url(image_links) left center/cover no-repeat;
}
```
Don't forget to edit the `image_link` with the real links ! Personnaly, I use a unsplash image.

# Convert code blocks to markdown

Some Obsidian's plugin use codeblocks to do some things, as [Agtable](https://github.com/windily-cloud/obsidian-AGtable) or [Table extended](https://github.com/aidenlx/table-extended)

To automatically convert these block to markdown, I use a mini plugin I wrote : [Mkdocs Custom Fence](https://github.com/Mara-Li/mkdocs_custom_fences)
To use it :
- Add `mkdocs_custom_fences` in your [requirements](https://github.com/Mara-Li/obsidian-mkdocs-publisher-template/blob/main/requirements.txt)
- Edit the [mkdocs.yml](https://github.com/Mara-Li/obsidian-mkdocs-publisher-template/blob/d7b7d43ff237c09e0cbf160889dcdac4b9459dfd/mkdocs.yml#L70) as follow : 
  ```yml
  markdow_extensions:
  pymdownx.superfences:
      custom_fences:
        - name: md-render
          class: md-render
          format: !!python/name:mkdocs_custom_fences.md_render.md_sub_render
  ```

For example, for AGtable : 
```yml
  - pymdownx.superfences:
      custom_fences:
        - name: agtable
          class: agtable
          format: !!python/name:mkdocs_custom_fences.md_render.md_sub_render
```
