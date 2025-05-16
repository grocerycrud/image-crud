Image CRUD
==========

[![Total Downloads](https://poser.pugx.org/grocerycrud/image-crud/downloads.png)](https://packagist.org/packages/grocerycrud/image-crud)

Image CRUD is an automatic multiple image uploader for Codeigniter, using the same philosophy as grocery CRUD library. 
Just some simple lines of code and you have all the functionality that you need.

Requirements:

- Codeigniter version 4
- PHP version 8 or higher
- PHP GD2 extension
- Composer

Installation:

```bash
composer require grocerycrud/image-crud
cp vendor/grocerycrud/image-crud/src/ImageCrud/ImageCrudPublisher.php app/Publishers
php spark publish
```

Controller Example:

```php
<?php

namespace App\Controllers;

use ImageCrud\Core\ImageCrud;

class ImagesExamples extends BaseController
{

    private function _example_output($output = null) {
        if (isset($output->isJSONResponse) && $output->isJSONResponse) {
            header('Content-Type: application/json; charset=utf-8');
            echo $output->output;
            exit;
        }

        return view('image_crud/template.php', (array)$output);
    }

    public function example1(): string
    {
        $imageCrud = new ImageCrud();

        $imageCrud->setPrimaryKeyField('id');
        $imageCrud->setUrlField('url');
        $imageCrud->setTable('example_1')
            ->setImagePath('uploads');

        $output = $imageCrud->render();

        return $this->_example_output($output);
    }
}
```

Limitations:

Since this is basically the same library as we used for Codeigniter 3, it has the same limitations.
- Image CRUD only works when the url that loads it is a standard Controller / View path. For example: 
  `/controller/method`. This will most probably change in the future

https://www.grocerycrud.com/image-crud-codeigniter-4