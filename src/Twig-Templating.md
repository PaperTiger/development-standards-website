{% include _includes/nav.md %}

# Folders & Files

### layout/main.twig
This file house the base html for the site. All js/css/html will eventually be fed into this file.

### _app-scripts.twig
This file handles adding the scripts to the end of the body. Since we are using webpack to generate a manafest.json file, we will use Craft to read the json and get the path.

You can find the craft variables which are set in `config/general.php`:
```php
 'assetsManifest' => (array)$assetsManifest,
 'assetsManifestLegacy' => (array)$assetsManifestLegacy,
```

### _includes

### pages