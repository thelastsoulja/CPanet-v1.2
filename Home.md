## What is this?
The XMWS PHP API client attempts to provide a PHP developer a simple class to connect to a given ZPanelX server and make web service requests using the XMWS (ZPanel**X** **M**odular **W**eb **S**ervice) web service, the API Client (PHP Class) also has a few utility methods to enable the developer easily handle XML data using standard PHP arrays.

If you have any questions on how to use this class please email: bobbyallen.uk@gmail.com

## About the developer
Bobby Allen is the head developer and project leader of the ZPanel project.

## Example usage
This example simply connects to a ZPanel server and returns a list of all domains hosted on the server.

`<?php
include 'xmwsclient.class.php';
$alldomains = new xmwsclient();
$alldomains->InitRequest('http://localhost/zpanelx/', 'bind', 'GetAllDomains', 'ee8795c8c53bfdb3b2cc595186b68912');`
$alldomains->SetRequestData('');
$response_data = $alldomains->ResponseToArray($alldomains->Request($alldomains->BuildRequest()));

// We now have the response data in an array in $response_data, so now we can use the content of $reponsedata['data'] (which is XML) and then we parse it through a utility class to convert it to a PHP array like so:-

$rows = XMLDataToArray($response_data['data'], 0);

// Now we can loop through all the domains echo'ing out the data.
foreach ($rows as $row){
   echo $row['domain']. ' ' .$row['path']. ' ' . $row['uid']; 
}
?>`
