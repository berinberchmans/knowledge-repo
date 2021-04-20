---
description: Uploading file to a server using php.
---

# Uploading files to server

In this example I am trying to upload a JSON file. Please substitute your file name in place of  `file_name` . You can add the file types that can be added in `$allowed` .

```text
<?php
if (isset($_POST['submit'])) {
  $file = $_FILES['file_name'];
  // print_r($file);
  $fileName = $_FILES['file_name']['name'];
  $fileTmpName = $_FILES['file_name']['tmp_name'];
  $fileSize = $_FILES['file_name']['size'];
  $fileError = $_FILES['file_name']['error'];
  $fileType = $_FILES['file_name']['type'];

  $fileExt = explode('.', $fileName);
  $fileActualExt = strtolower(end($fileExt));

  $allowed = array('json');

  if (in_array($fileActualExt, $allowed)) {
    if ($fileError === 0) {
      if($fileSize < 10000000){
          $target_dir = "directory/file_name.json";
          move_uploaded_file($fileTmpName,$target_dir);
          header("Location: index.html?uploadsuccess");
      }else{
        echo "File too big!";
      }
    }else{
      echo "Error uploading file!";
    }
  } else {
    echo "Upload the file_name.json file!";
  }
}
```

