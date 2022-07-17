Belongs To One Relation for Laravel 9.x
=====================================

![Travis CI](https://travis-ci.org/Byancode/belongs-to-one.svg?branch=master)

Based on [Belongs To Many](https://laravel.com/docs/5.3/eloquent-relationships#defining-relationships) Relation. Returns one model instead of Collection of models.

### Installation

``` composer require byancode/belongs-to-one```

### Usage

BelongsToOne relation is almost identical to standard BelongsToMany except it returns one model instead of Collection of models and ```null``` if there is no related model in DB (BelongsToMany returns empty Collection in this case). Include ```Byancode\Database\Eloquent\Relations\BelongsToOneTrait``` within your Model and use BelongsToOne relation.

Example:

```php
<?php

namespace App\Models;

use App\Models\Group;
Use Illuminate\Database\Eloquent\Model;
use Byancode\Database\Eloquent\Relations\BelongsToOneTrait;

class Record extends Model
{
    use BelongsToOneTrait;
    
    public function group()
    {
        return $this->belongsToOne(Group::class);
    }
}
```

And then use it like any other relation:
```php
$record = Record::with('group')->first();
```

### Testing
```./vendor/bin/phpunit```
