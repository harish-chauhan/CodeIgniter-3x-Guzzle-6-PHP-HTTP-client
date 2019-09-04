# CodeIgniter-3x-Guzzle-6-PHP-HTTP-client
============================================
Guzzle 6.0 PHP HTTP client integration with CodeIgniter 3.x

## Installing Guzzle

The recommended way to install Guzzle 6.0 is the official Guzzle Documentation.

```bash

Here is the link for official Guzzle Documentation:: http://docs.guzzlephp.org/en/stable/index.html

```

Or Please follow the following steps to install it

Clone or Download the Guzzle from the git repository

```bash
# Install guzzle files in application/libraries folder

git clone https://github.com/harish-chauhan/CodeIgniter-3x-Guzzle-6-PHP-HTTP-client.git

```

# Place the file and folder inside the application/libraries folder

```bash

Guzzel_PHP_HTTP.php
Guzzel_PHP_HTTP_vendor

```
Now Guzzel_PHP_HTTP_vendor and Guzzel_PHP_HTTP.php files successfully installed in the CodeIgniter 3.x applications/libraries folder

#To

```bash
	
	$this->load->library('Guzzel_PHP_HTTP');

	$client = new \GuzzleHttp\Client();

	// Set various headers on a request
	$response = $client->request('POST', 'https://api-prod.corelogic.com/trestle/oidc/connect/token', [
	    'form_params' => [
	        'grant_type' => 'client_credentials',
	        'scope' => 'api',
	        'client_id' => 'trestle_ZogoloIncBETACRM20190827120101',
	        'client_secret' => '0aaa74545e92450fbb86e83d382354f0',
	    ]
	]);

	$response_status = $response->getStatusCode(); # 200

	if ($response_status == 200) 
	{
		$trestle_response = $response->getBody(); # '{"id": 1420053, "name": "guzzle", ...}'
		$trestle_response = json_decode($trestle_response, true);

		echo "<pre>"; print_r($trestle_response); echo "</pre>";

		echo 'access_token:: '.$trestle_response['access_token']."<br>";
		echo 'token_type:: '.$trestle_response['token_type']."<br>";
		echo 'expires_in:: '.$trestle_response['expires_in']."<br>";
	}
	else
	{
		die('There is some error in this operation... .. .');
	}

```

Or you can also try the following code to access guzzle 6.0

```bash
  #guzzle library add to use guzzle
  $this->load->library('guzzle');

  # guzzle client define
  $client     = new GuzzleHttp\Client();
  
  #This url define speific Target for guzzle
  $url        = 'http://www.google.com';

  #guzzle
  try {
    # guzzle post request example with form parameter
    $response = $client->request( 'POST', 
                                   $url, 
                                  [ 'form_params' 
                                        => [ 'processId' => '2' ] 
                                  ]
                                );
    #guzzle repose for future use
    echo $response->getStatusCode(); // 200
    echo $response->getReasonPhrase(); // OK
    echo $response->getProtocolVersion(); // 1.1
    echo $response->getBody();
  } catch (GuzzleHttp\Exception\BadResponseException $e) {
    #guzzle repose for future use
    $response = $e->getResponse();
    $responseBodyAsString = $response->getBody()->getContents();
    print_r($responseBodyAsString);
  }


```