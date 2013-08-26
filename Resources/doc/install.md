# Installation

If not already done, install and configure [SonataMediaBundle](http://sonata-project.org/bundles/media/master/doc/index.html).

Then, add CoopTilleulsCKEditorSonataMediaBundle and IvoryCKEditorBundle in your `composer.json` file:

```json
{
    "require": {
        "tilleuls/ckeditor-sonata-mediabundle": "dev-master",
        "egeloen/ckeditor-bundle": "2.*"
    }
}
```

Register the bundle in your AppKernel:

```php
// app/AppKernel.php

public function registerBundles()
{
    return array(
        // ...
        new CoopTilleuls\Bundle\CKEditorSonataMediaBundle\CoopTilleulsCKEditorSonataMediaBundle(),
        new Ivory\CKEditorBundle\IvoryCKEditorBundle(),
        // ...
    );
}
```

Install bundles:

```
$ composer update
```

Configure IvoryCKEditorBundle to use the bundle as file browser:

```yaml
# app/config/config.yml

ivory_ck_editor:
    default_config: default
    configs:
        default:
            filebrowserBrowseRoute: admin_sonata_media_media_browser
            filebrowserImageBrowseRoute: admin_sonata_media_media_browser
            # Display images by default when clicking the image dialog browse button
            filebrowserImageBrowseRouteParameters:
                provider: sonata.media.provider.image
            filebrowserUploadRoute: admin_sonata_media_media_upload
            filebrowserUploadRouteParameters:
                provider: sonata.media.provider.file
            # Upload file as image when sending a file from the image dialog
            filebrowserImageUploadRoute: admin_sonata_media_media_upload
            filebrowserImageUploadRouteParameters:
                provider: sonata.media.provider.image
                context: my-context # Optional, to upload in a custom context
```

## Usage without IvoryCKEditorBundle

This bundle can be used with a custom install of CKEditor.
Read the [file browser (uploader)](http://docs.cksource.com/CKEditor_3.x/Developers_Guide/File_Browser_(Uploader)) doc of CKEditor and the [architecture](architecture.md) of this bundle.