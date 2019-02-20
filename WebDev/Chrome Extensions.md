# Chrome Extensions

1. Create a manifest file like so
```JSON
{
    "name": "Medium Bookmark Manager",
    "version": "1.0",
    "description": "Manage your Medium bookmarks – this is an unofficial application made by a fan of Medium who just wanted more functionality out of the bookmarks",
    "manifest_version": 2
  }
```
2. Unpack the directory in developer mode in the chrome extension tools
3. Register background scripts and other components in the `background` field so chrome knows what files to reference and how they should behave
4. Register APIs under the `permissions` field
5. Register `popups` in the `page_action` field
6. Register the toolbar icon under the `page_action`, then `default_icon`
7. Register the icons for display in the extension manager and elsewhere under the `icons` field