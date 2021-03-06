# Prospects

## Get Prospects By Title Or Company

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/prospect')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company_name' => 'toofr.com', 'title' => 'ceo', 'count' => 10)
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/prospect'
payload = {'key': 'abc123yourkeyhere', 'company_name': 'toofr.com', 'title': 'ceo', 'count': 10}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/prospect?key=abc123yourkeyhere&company_name=toofr.com&title=ceo&count=10
```

> The above command returns JSON structured like this:

```json
{
  "id":137,
  "name":"My first file upload",
  "description":"Prospects generated from web scrape.", 
  "created_at":"2017-05-20T20:55:44.635Z", 
  "state":"finished",
  "records_count_in":5,
  "records_count_processed":5
}
```

This endpoint creates a list in your account of new prospects that match your submitted criteria. You'll receive a JSON response of a new list which will contain your prospects. Refer to the List Records documentation for the call to view all records on a list.

### HTTP Request

`GET https://www.findemails.com/api/v1/prospect`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [FindEmails account page](https://www.findemails.com/account)
company_name | This is the text of either the company name or website.
title | This is a short title you want your prospects to have.
count | This is how many prospects you want to find.
tld | This is the country code you want to use. Default is USA.
page | Optional integer to get another page of results (10 returned per page, 1 credit per page response).

<aside class="success">
FindEmails works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
</aside>

### TLD Options

### Top-Level Domains (TLD)

Country | TLD
--------- | -----------
Afghanistan|af
Albania|al
Algeria|dz
Argentina|ar
Australia|au
Austria|at
Bahrain|bh
Bangladesh|bd
Belgium|be
Bolivia|bo
Bosnia and Herzegovina|ba
Brazil|br
Bulgaria|bg
Canada|ca
Chile|cl
China|cn
Colombia|co
Costa Rica|cr
Croatia|hr
Cyprus|cy
Czech Republic|cz
Denmark|dk
Dominican Republic|do
Ecuador|ec
Egypt|eg
El Salvador|sv
Estonia|ee
Finland|fi
France|fr
Germany|de
Ghana|gh
Greece|gr
Guatemala|gt
Hong Kong|hk
Hungary|hu
Iceland|is
India|in
Indonesia|id
Iran|ir
Ireland|ie
Israel|il
Italy|it
Jamaica|jm
Japan|jp
Jordan|jo
Kazakhstan|kz
Kenya|ke
Korea|kr
Kuwait|kw
Latvia|lv
Lebanon|lb
Lithuania|lt
Luxembourg|lu
Macedonia|mk
Malaysia|my
Malta|mt
Mauritius|mu
Mexico|mx
Morocco|ma
Nepal|np
Netherlands|nl
New Zealand|nz
Nigeria|ng
Norway|no
Oman|om
Pakistan|pk
Panama|pa
Peru|pe
Philippines|ph
Poland|pl
Portugal|pt
Puerto Rico|pr
Qatar|qa
Romania|ro
Russian Federation|ru
Saudi Arabia|sa
Singapore|sg
Slovak Republic|sk
Slovenia|si
South Africa|za
Spain|es
Sri Lanka|lk
Sweden|se
Switzerland|ch
Taiwan|tw
Tanzania|tz
Thailand|th
Trinidad and Tobago|tt
Tunisia|tn
Turkey|tr
Uganda|ug
Ukraine|ua
United Arab Emirates|ae
United Kingdom|uk
Uruguay|uy
Venezuela|ve
Viet Nam|vn
Zimbabwe|zw


## Get Prospects By Domain (database only)

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/get_prospects')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company_name' => 'findemails.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/get_prospects'
payload = {'key': 'abc123yourkeyhere', 'company_name': 'findemails.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/profile?key=abc123yourkeyhere&company_name=findemails.com
```

> The above command returns JSON structured like this:

```json
{
  "prospects":[
    {
      "first_name": "ryan",
      "last_name": "buckley",
      "title": "founder",
      "profile":{
        "fn":"Ryan Buckley",
        "photo":"https://media.licdn.com/dms/image/C4D03AQFIi292VtKikw/profile-displayphoto-shrink_200_200/0?e=1536192000&v=beta&t=aXWOwRlu17VF_r96euIeWvX00I8OYfOrwhaK-Xbmksg",
        "title":"Builder of ToOfr, Inlistio, and Voxloca. Author of The Parallel Entrepreneur. Resident of Contra Costa County.",
        "linkedin_profile":"https://www.linkedin.com/in/rbuckley"
      },
      "email":{
        "email":"ryan@toofr.com",
        "confidence":70,
        "state":"high"
      },
      "confidence_detail":{
        [
          {"description": "Mailserver score", "response": "+40"}, 
          {"description": "Pattern score", "response": "+27"}, 
          {"description": "MX records score", "response": "+10"}, 
          {"description": "Catchall score", "response": "+10"}, 
          {"description": "Uniqueness score", "response": "+2"}, 
          {"description": "List score", "response": "+2"}, 
          {"description": "Name score", "response": "+2"}, 
          {"description": "Disposable score", "response": "+2"}, 
          {"description": "Gibberish score", "response": "+2"}
        ]
      }
    },
  ]
}
```

This endpoint returns the emails and prospect data we have on a given domain in our database.

### HTTP Request

`GET https://www.findemails.com/api/v1/get_prospects`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [FindEmails account page](https://www.findemails.com/account)
company_name | The company name or domain of the business



## Get Profiles

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.findemails.com/api/v1/profile')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'first_name' => 'ryan', 'last_name' => 'buckley', 'email' => 'ryan@toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.findemails.com/api/v1/profile'
payload = {'key': 'abc123yourkeyhere', 'first_name': 'ryan', 'last_name': 'buckley', 'email': 'ryan@toofr.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.findemails.com/api/v1/profile?key=abc123yourkeyhere&first_name=ryan&last_name=buckley&email=ryan@toofr.com
```

> The above command returns JSON structured like this:

```json
{
  "profile": {
    "fn":"Ryan Buckley",
    "photo":"https://media.licdn.com/mpr/mpr/shrinknp_200_200/p/3/000/063/38c/276e158.jpg",
    "title":"CEO of FindEmails",
    "linkedin_profile":"https://www.linkedin.com/in/rbuckley"
  }
}
```

This endpoint returns the profile data we have on a given prospect and attempts to fetch it in real-time if it's not in our database.

### HTTP Request

`GET https://www.findemails.com/api/v1/profile`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [FindEmails account page](https://www.findemails.com/account)
first_name | The first name of the prospect
last_name | The last name of the prospect
email | The known email address of the prospect
