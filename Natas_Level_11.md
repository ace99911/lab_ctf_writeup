# Natas Level 11
This level starts with a background color changer and a title that wrote** "Cookies are protected with XOR encryption"**
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/dd1c17ac%2D016d%2D44d2%2D970e%2D601f034bb2ae/XsAtNvKMhLImYcrKg4HWP2of2-uAxBHS2OcH_o30yDg=.png)
This level will have something to do with XOR encryption. 
XOR encryption is an encryption method that uses Exclusive Or (XOR) operation logic to encrypt the message. The way to encrypt the message is by doing XOR operation for each letter of the message with a different strings of letter as the key.
Just like the other earlier challenge, the sourcecode for the website is given to identify the vulnarability of the website.
## Source Code Review
```
$defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");
```
The data for the website seems to be stored in a single array, which looks like something that we could use it later.
```
function xor_encrypt($in) {
    $key = '<censored>';
    $text = $in;
    $outText = '';

    // Iterate through each character
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}
```
This is the website XOR encryption. The key used for encryption is not available for us to reverse it so we might need to find it somehow.
```
function loadData($def) {
    global $_COOKIE;
    $mydata = $def;
    if(array_key_exists("data", $_COOKIE)) {
    $tempdata = json_decode(xor_encrypt(base64_decode($_COOKIE["data"])), true);
    if(is_array($tempdata) && array_key_exists("showpassword", $tempdata) && array_key_exists("bgcolor", $tempdata)) {
        if (preg_match('/^#(?:[a-f\d]{6})$/i', $tempdata['bgcolor'])) {
        $mydata['showpassword'] = $tempdata['showpassword'];
        $mydata['bgcolor'] = $tempdata['bgcolor'];
        }
    }
    }
    return $mydata;
}
```
The load function takes the global $_COOKIE variable and _run base64 decode, xor encrypt and json decode in that order to decrypt the cookie and use it to set the bgcolor and showpassword data. There is also a regular expression check on the bgcolor data to make sure that it is in a right color format. This mean that the only user input is heavily checked and not a great place to check first.
```
function saveData($d) {
    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
}
```
The save function will json encode,xor encrypt and base 64 encode the data and set it into the "data" cookie. It means that we have an option to manipulate the cookie to maybe give us access to the password for the next level.
```
if($data["showpassword"] == "yes") {
    print "The password for natas12 is <censored><br>";
}
```
This line of code checks if the "showpassword" data is equal to "yes", and if it true, it will give the password for the next level. So the answer to this level is to somehow manipulate the data from the cookie to set "showpassword" from "no" to "yes".
## Manipulating the Cookie
First, we need to check for the cookie itself by opening Developer tools on the website.
```
data=HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D
```
with this data, we now somehow need to change it back to plaintext and modify it to allow us to get the password. The entire seems to be encoded in base64 with the `%3D` is just URL encoding for `=`, which is the a padding. Since based on the source code earlier, we already know that the data is just `array( "showpassword"=>"no", "bgcolor"=>"#ffffff")` , we could use one of the properties of XOR encryption which is the associative properties to get the key of the encryption back. We first need to make the cookie without the XOR encryption.
```Php
<!DOCTYPE html>
<html>
<body>

<?php
$default_data=array( "showpassword"=>"no", "bgcolor"=>"#ffffff");
echo base64_encode(json_encode($default_data));
?>

</body>
</html>
```
This is one of the way to create the cookie by using php. The result of the strings comes out to be  `eyJzaG93cGFzc3dvcmQiOiJubyIsImJnY29sb3IiOiIjZmZmZmZmIn0=`. After that we could use cyberchef to reverse the encrypted cookie with the cookie that we have to get the key of the encryption. 
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/dd1c17ac%2D016d%2D44d2%2D970e%2D601f034bb2ae/ykS0Z0HFcp7plxht4YVX410iy3e0H0fQ1FguvJiVdmc=.png)
After done reversing the encryption, we are left with the key of the encryption which is `eDWo` repeating. With the key now available to us, we could easily manipulate the cookie for the password.
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/dd1c17ac%2D016d%2D44d2%2D970e%2D601f034bb2ae/rBLwL_nxkBs4NNanavo_JKlT3Cj8AhPzRATt0mtkXLs=.png)
The new cookie is now HmYkBwozJw4WNyAAFyB1VUc9MhxHaHUNAic4Awo2dVVHZzEJAyIxCUc5 . Now just need to replace the old one with this and we should be able to have access to the password
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/dd1c17ac%2D016d%2D44d2%2D970e%2D601f034bb2ae/FtRlFzR2MSqbuVa15s9MMjR39C_ltd4ktzB9-4OC0xg=.png)
And there the password for the next level.
