# Open Banking Data API Examples

Here are some fully working code examples to utilise the Get Products and Get product Detail API's.

## Get Products

This API returns a list of products currently offered by the financial institution to the market.

`https://data.holder.com.au/cds-au/v1/banking/products`

**PHP**

```PHP
<?php

$url = "https://api.anz/cds-au/v1/banking/products";

$curl = curl_init($url);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);

$headers = array(
   "x-v: 2",
);
curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
//for debug only!
curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);

$resp = curl_exec($curl);
curl_close($curl);
var_dump($resp);

?>
```

**JavaScript**

```JavaScript
var url = "https://api.anz/cds-au/v1/banking/products";

var xhr = new XMLHttpRequest();
xhr.open("GET", url);

xhr.setRequestHeader("x-v", "2");

xhr.onreadystatechange = function () {
   if (xhr.readyState === 4) {
      console.log(xhr.status);
      console.log(xhr.responseText);
   }};

xhr.send();
```

**Python**

```Python
import requests
from requests.structures import CaseInsensitiveDict

url = "https://api.anz/cds-au/v1/banking/products"

headers = CaseInsensitiveDict()
headers["x-v"] = "2"


resp = requests.get(url, headers=headers)

print(resp.status_code)
```

**C#**

```C#
var url = "https://api.anz/cds-au/v1/banking/products";

var httpRequest = (HttpWebRequest)WebRequest.Create(url);

httpRequest.Headers["x-v"] = "2";


var httpResponse = (HttpWebResponse)httpRequest.GetResponse();
using (var streamReader = new StreamReader(httpResponse.GetResponseStream()))
{
   var result = streamReader.ReadToEnd();
}

Console.WriteLine(httpResponse.StatusCode);
```

**Curl**

```
#!/bin/bash

curl -X GET https://api.anz/cds-au/v1/banking/products -H "x-v: 2" 
```

## Get Product Detail

This API returns detailed information on a single product offered by the financial institutions.

`https://data.holder.com.au/cds-au/v1/banking/products/{productId}`