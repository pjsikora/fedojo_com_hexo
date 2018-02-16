---
title: WordPress - Disable all plugins without PHPMyAdmin
id: 730
categories:
  - WordPress
date: 2016-01-25 15:38:47
tags:
---

How many times some of your friends/customers has problem with Wordpress? You are checking and there is blank page or 500 error? Than you are checking logs and you see problem with some installed and active plugin. Disabling it without access to the WP Backend and PHPMyAdmin can be tricky so how to do it with short code?

Lets list all wp-options table. Here we can see that we have stored information about active plugins:

<pre class="lang:default decode:true " >&lt;?php
require_once('wp-config.php');

$servername = DB_HOST;
$username = DB_USER;
$password = DB_PASSWORD;
$dbname = DB_NAME;

$conn = mysqli_connect($servername, $username, $password, $dbname);

if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$sql = "SELECT * FROM wp_options";
$result = mysqli_query($conn, $sql);

if (mysqli_num_rows($result) &gt; 0) {
    while($row = mysqli_fetch_assoc($result)) {
        echo "id: " . $row["option_id"]. " - Name: " . $row["option_name"]. " " . $row["option_value"]." " . $row["autoload"]. "&lt;br&gt;";
    }
} else {
    echo "0 results";
}

mysqli_close($conn);
?&gt;
</pre> 

With code: 
<pre class="lang:default decode:true " >require_once('wp-config.php');

$servername = DB_HOST;
$username = DB_USER;
$password = DB_PASSWORD;
$dbname = DB_NAME;</pre> 
you are loading wp-config.php file and sets values of variables with login data for database in our current file.

Lets list all active plugins
<pre class="lang:default decode:true " >&lt;?php
<?php
require_once('wp-config.php');

$servername = DB_HOST;
$username = DB_USER;
$password = DB_PASSWORD;
$dbname = DB_NAME;

$conn = mysqli_connect($servername, $username, $password, $dbname);

if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

$sql = "SELECT * FROM wp_options WHERE option_name='active_plugins'";
$result = mysqli_query($conn, $sql);

if (mysqli_num_rows($result) > 0) {
    // output data of each row
    while($row = mysqli_fetch_assoc($result)) {
        echo "id: " . $row["option_id"]. " - Name: " . $row["option_name"]. " " . $row["option_value"]." " . $row["autoload"]. "
";
    }
} else {
    echo "0 results";
}

mysqli_close($conn);
?>

</pre> 

Lets disable all plugins:

<pre class="lang:default decode:true " >&lt;?php
require_once('wp-config.php');

$servername = DB_HOST;
$username = DB_USER;
$password = DB_PASSWORD;
$dbname = DB_NAME;

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);
// Check connection
if ($conn-&gt;connect_error) {
    die("Connection failed: " . $conn-&gt;connect_error);
}

$sql = "UPDATE wp_options SET option_value='' WHERE option_name='active_plugins'";

if ($conn-&gt;query($sql) === TRUE) {
    echo "Record updated successfully";
} else {
    echo "Error updating record: " . $conn-&gt;error;
}

mysqli_close($conn);
?&gt;
</pre> 

Remember that after your changes its recommended to remove this files from server because somebody else can check/disable your plugins!