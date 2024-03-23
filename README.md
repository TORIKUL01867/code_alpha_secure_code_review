# code_alpha_secure_code_review
#This is a project where I have tried to describe how to keep coding secure and safe from hackers.

<?php
// Vulnerable code: OS command injection can occur here
$filename = $_GET['filename'];
system("cat " . $filename);
?>

<!-- Improvements and advice -->
<!-- 1. Avoid directly using user input in system commands -->
<!-- 2. Sanitize and validate input before using it -->
<!-- 3. Limit input to only acceptable characters or values -->

<?php
// Improved code: Adding input validation and using safer alternatives
$allowed_files = ['file1.txt', 'file2.txt', 'file3.txt'];
$filename = $_GET['filename'];

// Check if the filename is in the allowed files list
if (in_array($filename, $allowed_files)) {
    // Use safer alternatives like file_get_contents to read file contents
    $file_contents = file_get_contents($filename);
    echo $file_contents;
} else {
    echo "Invalid filename!";
}
?>

