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
