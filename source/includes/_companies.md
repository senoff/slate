# Companies

## Get Prospects and Patterns

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/prospect')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/prospect'
payload = {'key': 'abc123yourkeyhere', 'company': 'toofr.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/prospect?key=abc123yourkeyhere&company=toofr.com
```

> The above command returns JSON structured like this:

```json
{ "prospects": {
  "domain":"toofr.com",
  "prospects":    
    [
      { 
        "email":"ryan@toofr.com", 
        "first_name":"Ryan",
        "last_name":"Buckley",
        "confidence":119,
        "profile": {
          "fn"=>"Ryan Buckley", "photo"=>"https://media.licdn.com/mpr/mpr/shrinknp_200_200/AAEAAQAAAAAAAAniAAAAJGU1MjAxMWI1LTU1ZDItNDQ3OS1iYWVlLWNhNTNhNmIzZWU1Yw.jpg", 
          "title"=>"Founder of Toofr.com, eNPS.co, and Thinboxapp.com", 
          "linkedin_profile"=>"https://www.linkedin.com/in/rbuckley"
        }
      },
      { 
        "email":"kurdt@toofr.com", 
        "first_name":"Kurt",
        "last_name":"Cobain",
        "confidence":89,
        "profile": {
          "fn"=>"Kurdt Cobain", "photo"=>"https://media.licdn.com/mpr/mpr/shrinknp_200_200/AAEAAQAAAAAAAAniAAAAJGU1MjAxMWI1LTU1ZDItNDQ3OS1iYWVlLWNhNTNhNmIzZWU1Yw.jpg", 
          "title"=>"Singer / songwriter", 
          "linkedin_profile"=>"https://www.linkedin.com/in/rbuckley"
        }
      },
      { 
        "email":"dave@toofr.com", 
        "first_name":"Dave",
        "last_name":"Grohl",
        "confidence":104,
        "profile": {
          "fn"=>"David Grohl", "photo"=>"https://media.licdn.com/mpr/mpr/shrinknp_200_200/AAEAAQAAAAAAAAniAAAAJGU1MjAxMWI1LTU1ZDItNDQ3OS1iYWVlLWNhNTNhNmIzZWU1Yw.jpg", 
          "title"=>"Drummer extraordinaire and future stadium rocker", 
          "linkedin_profile"=>"https://www.linkedin.com/in/rbuckley"
        }
      },
      { 
        "email":"krist@toofr.com", 
        "first_name":"Krist",
        "last_name":"Novoselic",
        "confidence":93,
        "profile": {
          "fn"=>"Krist Novoselic", "photo"=>"https://media.licdn.com/mpr/mpr/shrinknp_200_200/AAEAAQAAAAAAAAniAAAAJGU1MjAxMWI1LTU1ZDItNDQ3OS1iYWVlLWNhNTNhNmIzZWU1Yw.jpg", 
          "title"=>"The quiet bassist", 
          "linkedin_profile"=>"https://www.linkedin.com/in/rbuckley"
        }
      }
    ]
  },
  "top_pattern":
  [ "first name", "miles@toofr.com" ]
}
```

This endpoint delivers the prospects in our database based on company name or website.

### HTTP Request

`GET https://www.toofr.com/api/v1/prospect`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
company | This is the text of either the company name or website.

<aside class="success">
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
</aside>

## Get Company Industry and Agency Data

```ruby
require 'net/http'
require 'json'

uri = URI('https://www.toofr.com/api/v1/classify')
res = Net::HTTP.get(uri, 'key' => 'abc123yourkeyhere', 'company' => 'toofr.com')
JSON.parse(res.body)
```

```python
import requests

uri = 'https://www.toofr.com/api/v1/classify'
payload = {'key': 'abc123yourkeyhere', 'company': 'toofr.com'}
r = requests.get(uri, data = payload)
r.json()
```

```shell
curl https://www.toofr.com/api/v1/classify?key=abc123yourkeyhere&company=toofr.com
```

> The above command returns JSON structured like this:

```json
{
  "industry":"marketing_and_advertising",
  "agency_category":"advertising",
  "is_agency":"no"}
```

This endpoint uses our natural language processing engine to determine the industry and agency category and status of any website.

### HTTP Request

`GET https://www.toofr.com/api/v1/classify`

### Query Parameters

Parameter | Description
--------- | -----------
key | Your key is required for any request and is found on your [Toofr account page](https://www.toofr.com/account)
company | This is the text of either the company name or website.

<aside class="success">
Toofr works best when you give it websites or domains, but we'll also take company names. (e.g. apple.com works better than Apple). Company names take an additional credit.
</aside>

### Query Responses

Parameter | Description
--------- | -----------
industry | The general industry our artificial intelligence believes the website to be in.
is_agency | A boolean (true / false) response on whether we believe the company is an agency.
agency_category | If we believe the company is an agency, this is the more specific agency category it falls under. 