# **getGJUserInfo20.php**
Gets the account info of a specific user, supplied by their account ID.  
`https://www.boomlings.com/database/getGJUserInfo20.php`

## **Parameters**
| Name | Value | Type | Required? | Description |
|------|-------|------|-----------|-------------|
| targetAccountID | - | **Integer** | **✔** | The account ID of the user you want to get the information of. |
| secret | Wmfd2893gb7 | **String** | **✔** | A 'password' needed for all API requests. |
| gameVersion | 22 | **Integer** | ✖ | The version of Geometry Dash. |
| binaryVersion | 40 | **Integer** | ✖ | The version of the Geometry Dash servers. |
| gdw | 0 | **Integer** | ✖ | Whether the request is being made from Geometry Dash World. |
| accountID | - | **Integer** | ✖ | The account ID of the user making the request. |
| uuid | - | **Integer** | ✖ | The user ID of the user making the request. |
| udid | - | **String** | ✖ | ? |
| gjp2 | - | **GJP2** | ✖ | The GJP2 of the user making the request. |

!!! note
	Values of `-` are variable and should be supplied depending on the target user and the user making the request.

## **Response**
Returns a [user object](../../../resources/user) for the user you want the account info of.
!!! example
	```md
	1:Trigam:2:15765803:13:118:17:412:10:94:11:3:51:3:3:4283:52:223:46:15276:4:101:8:0:18:0:19:0:50:1:20:UCT12Cnpkd-6kQEewKv_kqbQ:21:376:22:129:23:30:24:83:25:26:26:34:28:1:43:29:48:15:53:12:54:2:30:117824:16:970465:31:0:44:Trigam04:45:TrigamDev:49:0:55:66,10,5,0,0,2,2,1,0,0,11,3:56:90,50,59,177,138,43,44,68:57:1,2,6,13,11,2,0:29:1
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