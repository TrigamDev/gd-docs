# **GJP**
The GJP is a string sent in many requests for account authentication. This used in place of simply sending the user's password in the request, which is obviously wildly insecure. There are two variations: [GJP](#gjp_1) (pre-2.2), and [GJP2](#gjp2) (2.2+).
!!! danger
	***NEVER*** send your GJP to *anyone* for *any* reason. Doing so will compromise your account!
## **GJP2**
GJP2 is a hash usually sent as the `gjp2` parameter in requests. It is created using the [SHA-1](https://en.wikipedia.org/wiki/SHA-1) hash function, and is formatted as a 20-byte, hexadecimal hash value, also known as a message digest.
???+ warning
	While hashing the password with salt is good practice and secure, Rob's implementation isn't for various reasons:

	- Hash salts should be random as to prevent the same input from producing the same output. That is the purpose of a salt. Having the salt as an unchanging, arbitrary string defeats the purpose of having a salt.

	- [SHA-1](https://en.wikipedia.org/wiki/SHA-1) has long since been considered insecure, and is susceptible to [chosen-prefix attacks](https://en.wikipedia.org/wiki/Collision_attack#Chosen-prefix_collision_attack). Many organizations have recommended it to be replaced with other hash functions, such as [SHA-2](https://en.wikipedia.org/wiki/SHA-2) or [SHA-3](https://en.wikipedia.org/wiki/SHA-3).
	
	Thank you, Rob.
### **Encoding**
The hash is created with the user's password and adds `mI29fmAnxgTs` as salt.  

Here is an example of how one could implement the encoding of the hash into code.
???+ example
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
### **Decoding**
While encoding a hash is simple enough to do, it cannot be decoded due to the one-way nature of a hash function. This does **not** mean it is safe to let others see the hash however, as this lets them make requests on your behalf.
## **GJP**
GJP is similar to GJP2, but is outdated and extremely insecure, hence the replacement with a newer version. Unlike GJP2, which uses a one-way hash function, GJP simply uses a combination of XOR encoding and base64 encoding, which can very easily be reversed.
???+ note
	While the Geometry Dash client uses GJP2 for all of the requests, most endpoints still accept the old GJP. It is recommended to avoid using this, however, due to the lack of security GJP has.
### **Encoding**
The GJP is made by taking the user's password, XOR encoding it using a key of `37526`, and then encoding it again with base64.  

Here is an example of how one could implement the encoding into code.
???+ example
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
		import base64

		# XOR encryption
		def xor_cipher(text, key):
			encrypted = ""
			for i in range(len(text)):
				encrypted += chr(ord(text[i]) ^ ord(key[i % len(key)]))
			return encrypted

		password = "password123" # Replace with user's password
		xor_encoded = xor_cipher(password, "37526")

		gjp = base64.b64encode(xor_encoded.encode()).decode()
		gjp.replace("+", "-")
		gjp.replace("/", "_")

		print(gjp)
		```