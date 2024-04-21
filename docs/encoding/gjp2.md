# **GJP2**
GJP2 is hash commonly sent as the `gjp2` parameter in many requests. It is used for account authentication, used in place of simply sending the user's password in the request, which is obviously wildly insecure.
## **Encoding**
The user's GJP2 is a hash, created using the [SHA-1](https://en.wikipedia.org/wiki/SHA-1) hash function. It takes in the user's password and adds `mI29fmAnxgTs` as salt, producing a 20-byte hash value.
!!! warning
	Hash salts should be random as to prevent the same input from producing the same output. That is the purpose of a salt. Having the salt as an unchanging, arbitrary string defeats the purpose of having a salt. Thank you, Rob.
!!! warning
	[SHA-1](https://en.wikipedia.org/wiki/SHA-1) has long since been considered insecure, and is susceptible to [chosen-prefix attacks](https://en.wikipedia.org/wiki/Collision_attack#Chosen-prefix_collision_attack). Many organizations have recommended it to be replaced with other hash functions, such as [SHA-2](https://en.wikipedia.org/wiki/SHA-2) or [SHA-3](https://en.wikipedia.org/wiki/SHA-3). Thank you, Rob.

### **Example**
Here is an example of how one could implement the encoding into code.
=== "JS"
	```js
	import crypto from "crypto"

	let hash = crypto.createHash("sha1")
	let password = 'password123' // Replace with the user's password
	let salt = "mI29fmAnxgTs"

	hash.update(password + salt)
	let gjp2 = hash.digest('hex')

	console.log(gjp2)
	```
=== "Python"
	```py
	import hashlib

	hash = hashlib.sha1()
	password = "password123" # Replace with user's password
	salt = "mI29fmAnxgTs"

	hash.update((password + salt).encode())
	gjp2 = hash.hexdigest()

	print(gjp2)
	```