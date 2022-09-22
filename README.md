# Installation & Configuration

## Installation

Download required package using below command.

```bash
  composer require "darkaonline/l5-swagger"
```

## Configuration

Open your `config/app.php` and add below line in `providers` section.

```bash
  L5Swagger\L5SwaggerServiceProvider::class,
```

You can publish L5-Swagger's config and view files into your project by running:

```bash
  php artisan vendor:publish --provider "L5Swagger\L5SwaggerServiceProvider"
  php artisan l5-swagger:generate
```
Copy the below `code` and past in `routes/api.php` file.

```php
Route::get('students', function(){
    return [
        "id"=> 1,
        "roll_number"=> 1001,
        "name"=> "Krishna Kanhaiya",
        "class"=> "XII"
    ];
});

Route::get('student-details/{student_id}', function(Request $request){
    return [
        "id"=> $request->student_id,
        "roll_number"=> 1001,
        "name"=> "Krishna Kanhaiya",
        "class"=> "XII"
    ];
});

Route::put('student-update/{student_id}', function(Request $request){
    return [
        "id"=> $request->student_id,
        "roll_number"=> 1001,
        "name"=> $request->name,
        "class"=> $request->class
    ];
});

Route::delete('student-delete/{student_id}', function(Request $request){
    return [
        "id"=> $request->student_id,
    ];
});

Route::post('student-add', function(Request $request){
    return [
        "id"=> 1,
        "roll_number"=> 1001,
        "name"=> $request->name,
        "class"=> $request->class
    ];
});
```

After that you have to download `api-docs.json` file from top and paste in the `storage/api-docs/` directory.

## Test you API Documentation.

Open below `URL` in the browser and use the API.

```url
  http://127.0.0.1:8000/api/documentation
```

`Optional`

## Change Path of API Documentation

Open file `config/l5-swagger.php` and change the URL of API documentation using below.

```url
  documentations > default > routes > api => 'your_url'
```

## Modify swagger API Documentation.

Open file `storage/api-docs/api-docs.json` and modify your URL.
