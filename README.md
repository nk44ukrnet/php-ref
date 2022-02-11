# php-ref

___print file extension___
```
$extName = 'file.exe.png.pdf.jpg';
$ext = pathinfo($extName, PATHINFO_EXTENSION);

echo $ext;
```


___basic file upload validation___
```
$errorMessage = '';
if (isset($_FILES['file'])) {
    //var_dump($_FILES);
    $file = $_FILES['file'];

    $ext = pathinfo($file['name'], PATHINFO_EXTENSION);
    $ext = strtolower($ext);

    $allowedExtensions = ['jpg', 'png', 'gif'];

    if ($file['size'] > 5 * 1024 * 1024) { //5 mb
        $errorMessage = 'You can not upload files greater than 5 MB';
    } elseif (!in_array($ext, $allowedExtensions)) {
        $errorMessage = 'You can only upload Images';
    } else {
    move_uploaded_file($_FILES['file']['tmp_name'], './uploads/_' . time() . '_' . rand(1, 50000) . '_' . $_FILES['file']['name']);
    }
}
```

___working with filesystem___

```
// Magic constants
//__FILE__ - filename + path
//__DIR__ + path

// Create directory
//mkdir('test');

// Rename directory
//rename('test', 'test1');

// Delete directory
//rmdir('test1');

// Read files and folders inside directory
//scandir('./'); //returns array

// file_get_contents, file_put_contents
//$text = file_get_contents('lorem.txt');
//file_put_contents('lorem.txt', 'My content' . PHP_EOL . $text);

// https://www.php.net/manual/en/book.filesystem.php
// file_exists
// is_dir
// filemtime
// filesize
// disk_free_space
// file
```
