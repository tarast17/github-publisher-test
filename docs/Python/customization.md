---
share: true
---

- You can prevent the script to share file in specific folder, with editing `folder` list in `exclude.yml`
- You can prevent the script to **delete** some file with editing `file` list in the same file.
- You can, also, create some CSS customization with hashtag, with editing `docs/assets/css/custom_attributes.css`. See [[Template/customization#custom-attribute]] for some example.

## Folder note

To support the citation and link to these page, you need to use an index key (cf [[Python/usage#script-s-configuration]]).

Some examples of citation and their transformation : 

| In Obsidian               | In Publish            |
| ------------------------- | --------------------- |
| `[[Real File\|(i) Alias]]` | `[[index\|Alias]]`     |
| `[[Real File\|(i)]]`       | `[[index\|Real File]]` |
| `[(i) Alias](Real file) ` | `[Alias](index)`      |
| `[(i)](real file)`        | `[real file](index)`  | 