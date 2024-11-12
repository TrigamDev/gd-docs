# **getGJUserInfo20.php**
`https://www.boomlings.com/database/getGJUserInfo20.php`

Gets the account info of a specific user, supplied by their account ID.  

## **Parameters**
| Name | Value | Type | Required? | Description |
|------|-------|------|-----------|-------------|
| targetAccountID | - | **Integer** | **✔** | The account ID of the user you want to get the information of. |
| secret | Wmfd2893gb7 | **String** | **✔** | A 'password' needed for all API requests. |
| gameVersion | 22 | **Integer** | ✖ | The version of Geometry Dash. |
| binaryVersion | 42 | **Integer** | ✖ | The version of the Geometry Dash servers. |
| gdw | 0 | **Integer** | ✖ | Whether the request is being made from Geometry Dash World. |
| accountID | - | **Integer** | ✖ | The account ID of the user making the request. |
| uuid | - | **Integer** | ✖ | The user ID of the user making the request. |
| udid | - | **String** | ✖ | The [UDID](site:encoding/udid) |
| gjp2 | - | **GJP2** | ✖ | The GJP2 of the user making the request. |

!!! note
	Values of `-` are variable and should be supplied depending on the target user and the user making the request.

## **Response**
Returns a [user object](site:server/resources/user) for the user you want the account info of.
!!! example
	```md
	1:RobTop:2:16:13:20:17:175:10:35:11:2:51:0:3:2966:52:180:46:3259:4:5:8:0:18:2:19:1:50:0:20:UCz_yk8mDSAnxJq0ar66L4sw:21:483:22:1:23:1:24:1:25:1:26:1:28:0:43:1:48:1:53:1:54:1:30:258348:16:71:31:0:44:RobTopGames:45:robtopgames:49:2:55:2,2,1,0,0,0,0,0,0,0,0,0:56:51,32,82,280,105,20,71,5:57:0,3,6,21,6,2,0:29:1
	```

## **Example**
Here is a basic example of how one could implement this in code.
=== "JS"
	```js
	import axios from "axios"

	let data = {
		"targetAccountID": 970465,
		"secret": "Wmfd2893gb7"
	}
	let headers = {
		"User-Agent": "",
		"Content-Type": "application/x-www-form-urlencoded"
	}

	let req = await axios.post("https://www.boomlings.com/database/getGJUserInfo20.php", data, { headers })
	console.log(req.data)
	```
=== "Python"
	```py
	import requests

	data = {
		"targetAccountID": 970465,
		"secret": "Wmfd2893gb7"
	}
	headers = {
		"User-Agent": "",
		"Content-Type": "application/x-www-form-urlencoded"
	}

	req = requests.post("https://www.boomlings.com/database/getGJUserInfo20.php", data = data, headers = headers)
	print(req.text)
	```