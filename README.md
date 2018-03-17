# Public Upload API for Project AcgnX Torrent Glogal

> "Project AcgnX Torrent Glogal" is too long, So the following is referred to as "P.A.T.G".

> Frist, you will need to enable API functionality on your P.A.T.G account: https://www.acgnx.se/user.php?o=myapi

> Warning: Do not post too many requests at the same time! because they will be blocked by FireWall. 

## What is Public Upload API for P.A.T.G?

API submissions let you submit things from an automated process without using cookies to store your login session. Anyone with your API Token can submit stuff as you, so make sure you keep your API Token secret. Renew API Token if you think your token has been compromised.

## Who can use Public Upload API for P.A.T.G?

Anyone. But you should have a P.A.T.G account frist. And you should be know your must be agreed to the [《AcgnX Torrent Global Terms of Service》](https://www.acgnx.se/tos.html) if you sign in our account.

## How to Enable API functionality on my P.A.T.G account?

Click here to visit your account API setting page to enable this functionality: https://www.acgnx.se/user.php?o=myapi

## How to use?

After your account API functionality is enable, you can refer to this HTML Demo page for reference development: https://www.acgnx.se/demo/apidemo.html

An example program you can use is cURL, whose command line is like:

> curl 'https://www.acgnx.se/user.php?o=api&op=upload' -F "mod=upload" -F "sort_id=25" -F "bt_file=@/path/test.torrent" -F "title=This is a test from Curl API" -F "intro=just a test." -F "uid=YOUR_ACCOUNT_UID" -F "api_token=YOUR_ACCOUNT_API_TOKEN"

If you encounter SSL errors, adding '-k' may solve the problem.

> Warning: Do not post too many requests at the same time! because they will be blocked by FireWall. 

We recommend using 'multipart/form-data' to encode, that can prevents coding errors from upload.

You need to specify the type "mod" as "Upload".

The server will be return a message of JSON to display status in after uploaded.

## Upload parameters

The following will explain all the upload parameters:

### 1.1 "mod"

Example:

> mod = upload

Importance: Must. function Selection of API. But only have "upload" now.

### 1.2 "sort_id"

Example:

> sort_id = 25

Importance: Must. Sort Selection of upload. Detailed classification can refer to the following "Sort ID" content.

### 1.3 "bt_file"

Example:

> bt_file=@/path/test.torrent

Importance: Must. Need to strictly upload the HTTP protocol upload file standard.

### 1.4 "title"

Example:

> title = This is a test from Curl API

Importance: Must. The length of the resource title name should be limited to 1 - 400 characters or less.

### 1.5 "intro"

Example:

> intro = just a test.

Importance: Optional. But if you choose to fill in, The length of the resource description should be limited to 40000 characters or less.

### 1.6 "emule_resource"

Example:

> emule_resource = ed2k://|file|eMule0.49c.zip|2868871|0F88EEFA9D8AD3F43DABAC9982D2450C|/

Importance: Optional. Upload eMule resources, Each line an ED2K Link (use CRLF "\r\n" to line feed ).

### 1.7 "synckey"

Example:

> synckey = BI3ACGSYU7DTURRU44AKLJ6FQNYXZG64P

Importance: Optional. [What is the Resilio Sync?](https://en.wikipedia.org/wiki/Resilio_Sync)

### 1.8 "discuss_url"

Example:

> discuss_url = https://www.acgnx.se/feedback.php

Importance: Optional. Only support HTTP/HTTPS URL.

### 1.9 "Anonymous_Post"

Example:

> Anonymous_Post = 0

Importance: Optional. Default 0. 0 = Not Anonymous Post. 1 = Post by Anonymous.

### 1.10 "Team_Post"

Example:

> Team_Post = 0

Importance: Optional. Default 0. 0 = Post by Personal. 1 = Post by union.

### 1.11 "uid"

Example:

> uid = 10001

Importance: Must. Your account UID. You can getting in API Setting page: https://www.acgnx.se/user.php?o=myapi

### 1.12 "api_token"

Example:

> api_token = xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Importance: Must. Your account API Token. You can getting in API Setting page: https://www.acgnx.se/user.php?o=myapi

## Sort ID

Example:

> Sort_full_name = Sort_display_name = Sort_ID

### Anime 

>* Anime English Translated = A.E.T = 2
>* Anime Raw = A.Raw = 3
>* Anime Non English Translated = A.N.E.T = 4
>* Anime Music Video = A.M.V = 5

### Audio

>* Lossless = Lossless = 7
>* Lossy = Lossy = 8

### Literature

>* Literature English Translated = L.E.T = 10
>* Literature Raw = L.Raw = 11
>* Literature Non English Translated = L.N.E.T = 12

### Live Action

>* Live Action English Translated = L.A.E.T = 14
>* Live Action Raw = L.A.Raw = 15
>* Live Action Non English Translated = L.A.N.E.T = 16
>* Live Action Idol/Promotional Video = Idol/PV = 17

### Software

>* Applications = Applications = 19
>* Games = Games = 20

### Pictures

>* Photos = Photos = 22
>* Graphics = Graphics = 23

### Ohter

>* Other = Other = 25

## Server Answer Message

If upload successful, the Server will be return "code" as "200" of a message of JSON. But if have any error, that will be show in type "value".

### Upload Successful

If successful, Server will be return a message of JSON with this Example:

> {"status":"success","code":"200","infohash":"xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx","title":"This is a test from Curl API"}

You can getting infohash of your uploaded torrent file in "infohash", So you can use this infohash to synthesize the URL address of this torrent: 

> https://www.acgnx.se/show-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.html

### Upload Unsuccessful

If unsuccessful by torrent already exists, Server will be return a message of JSON with this Example:

> {"status":"error","code":"302","value":"torrent already exists","infohash":"xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx","title":"This is a test from Curl API but Not you"}

If unsuccessful by auth failed, Server will be return a message of JSON with this Example:

> {"status":"error","code":"105","value":"auth failed"}

### Other Unsuccessful Message

>* Code 10x: API and User Authentication Control System Private error code. start from 101.
>* Code 30x: Upload format error and torrent already exists Private error code. start from 301.
>* Code 40x: POST Data requests format error Private error code.

## Other Question

>* Q: Did you have limit of everyday upload count?
>* A: No.

>* Q: I don't know what I want to asking.
>* A: Please contact us if you need help: support@acgnx.se (Only English Support)


# Project AcgnX Torrent Global All rights reserved.
