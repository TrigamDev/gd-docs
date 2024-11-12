# **Server User Resource**
## **User**
Each player of Geometry Dash has a profile containing various types of data, such as info, stats, completed levels, icons, and connected socials.

A typical user server response is structured with a `key:value:key:value` pairing.

!!! example
	```
	1:Trigam:2:15765803:13:118:17:568:10:94:11:3:51:3:3:5568:52:446:46:20404:4:152:8:0:18:0:19:0:50:1:20:UCT12Cnpkd-6kQEewKv_kqbQ:21:376:22:129:23:30:24:83:25:26:26:34:28:1:43:29:48:15:53:12:54:2:30:83343:16:970465:31:0:44:Trigam04:45:TrigamDev:49:0:55:83,14,4,0,0,5,5,2,0,0,18,20:56:93,54,62,201,178,55,67,109:57:1,6,10,21,22,5,0:29:1
	```

## **Keys**
Each `key` is tied to a component within the client and the `value` contains the data for that component.

#### **List of Keys**
| Key | Name  | Type | Description |
|:---:|------|------|-------------|
| `1` | Username **String** | The username of the user |
| `2` | User ID | **Integer** | The ID of user |
| `3` | Stars | **Integer** | The number of stars the user has earned |
| `4` | Demons | **Integer** | The number of demon levels the user has completed |
| `6` | Ranking | **Integer** | The global leaderboard position of the user |
| `7` | Account Highlight | **Integer** | The Account ID of the user, used for highlighting the user on the leaderboards |
| `8` | Creator Points | **Integer** | The number of creator points the user has earned |
| `9` | Display Icon | **Integer** | The ID of the display icon |
| `10` | Primary Color | **Integer** | The chosen primary user color |
| `11` | Secondary Color | **Integer** | The chosen secondary user color |
| `13` | Secret Coins | **Integer** | The number of secret coins the user has collected |
| `14` | Display Icon Type | **Integer** | The type of the display icon |
| `15` | Special | **Integer** | Use is unknown, usually the same for all users |
| `16` | Account ID | **Integer** | The account ID of the user |
| `17` | User Coins | **Integer** | The number of user coins the user has collected |
| `18` | Message State | **Integer** | Who the user allows messages from (`0`: All, `1`: Friends, `2`: None) |
| `19` | Friend Request State | **Integer** | Who the user allows friend requests from (`0`: All, `1`: None) |
| `20` | YouTube | **String** | The YouTube URL the user has linked |
| `21` | Icon | **Integer** | The ID of the icon the user has chosen |
| `22` | Ship | **Integer** | The ID of the ship the user has chosen |
| `23` | Ball | **Integer** | The ID of the ball the user has chosen |
| `24` | UFO | **Integer** | The ID of the UFO the user has chosen |
| `25` | Wave | **Integer** | The ID of the wave the user has chosen |
| `26` | Robot | **Integer** | The ID of the robot the user has chosen |
| `27` | Trail | **Integer** | The ID of the trail the user has chosen |
| `28` | Glow | **Integer** | Whether the user has glow activated |
| `29` | Registered | **Integer** | Whether the user's account has been registered |
| `30` | Global Rank | **Integer** | The rank of the user on the global leaderboard |
| `31` | Friend State | **Integer** | Whether the user is friends with a target user (`0`: Not friends, `1`: Already friends, `3`: Sent request to target, `4`: Target sent request) |
| `38` | Messages | **Integer** | How many new messages the user has |
| `39` | Friend Requests | **Integer** | How many new friend requests the user has |
| `40` | New Friends | **Integer** | How many new friends the user has |
| `41` | New Friend Request | **Bool** | If the friend request from this user is new |
| `42` | Age | **String** | The time since the user has submitted a levelScore |
| `43` | Spider | **Integer** |The ID of the spider the user has chosen |
| `44` | Twitter | **String** | The Twitter URL the user has linked |
| `45` | Twitch | **String** | The Twitch URL the user has linked |
| `46` | Diamonds | **Integer** | The number of diamonds the user has earned |
| `48` | Death Effect | **Integer** | The ID of the death effect the user has chosen |
| `49` | Mod Level | **Integer** | The type of moderator the user is (`0`: Not a mod, `1`: Mod, `2`: Elder Mod) |
| `50` | Comment History State | **Integer** | Who the user allows to see their comment history (`0`: All, `1`: Only friends, `2`: None) |
| `51` | Glow Color | **Integer** | The chosen glow color |
| `52` | Moons | **Integer** | The number of moons the user has earned |
| `53` | Swing | **Integer** |The ID of the swing the user has chosen |
| `54` | Jetpack | **Integer** |The ID of the jetpack the user has chosen |
| `55` | Demon List | **String** | A list of all of the demons the user has completed |
| `56` | Level List | **String** | A list of all of the levels the user has completed |
| `57` | Platformer Level List | **String** | A list of all of the platformer levels the user has completed |

!!! note
	In keys `20` (YouTube), `44` (Twitter), and `45` (Twitch), only the user-specific part of the URL is stored. In order to get the URL, you must prepend them with the website URL.  
	> If key `20` were to be `UCT12Cnpkd-6kQEewKv_kqbQ`, you must prepend 'https://www.youtube.com/channel/' to get the full, usable URL

### **Level Lists**
Multiple lists of levels are stored in the user resource, which are formatted as an ordered, comma-seperated list. These are to keep track of the user's completed demons, levels, and platformer levels for display in the profile.

#### **Demon List**
A user's demon list contains all of the demon levels the user has completed.  
From left to right, it is in the order of:

- Easy, Medium, Hard, Insane, Extreme, Platformer Easy, Platformer Medium, Platformer Hard, Platformer Insane, Platformer Extreme, Weekly, Gauntlet

!!! example
	```md
	83,14,4,0,0,5,5,2,0,0,18,20
	```

#### **Level List**
A user's level list contains all of the classic levels the user has completed.  
From left to right, it is in the order of:

- Auto, Easy, Normal, Hard, Harder, Insane, Daily, Gauntlet

!!! example
	```md
	93,54,62,201,178,55,67,109
	```

#### **Platformer Level List**
A user's platformer level list contains all of the platformer levels the user has completed.  
From left to right, it is in the order of:

- Auto, Easy, Normal, Hard, Harder, Insane

!!! example
	```md
	1,6,10,21,22,5,0
	```

## **Parsed User Example**
???+ example
	```json
	{
		info: {
			username: "Trigam",
			userId: 15765803,
			globalRank: 83343,
			accountId: 970465,
			modLevel: "none",
		},
		stats: {
			levels: {
				classic: {
					auto: 93,
					easy: 54,
					normal: 62,
					hard: 201,
					harder: 178,
					insane: 55,
					daily: 67,
					gauntlet: 109,
					total: 819,
					unique: 643,
				},
				platformer: {
					auto: 1,
					easy: 6,
					normal: 10,
					hard: 21,
					harder: 22,
					insane: 5,
					total: 65,
					unique: 65,
				},
				total: 884,
				unique: 708,
			},
			secretCoins: 118,
			userCoins: 568,
			stars: 5568,
			moons: 446,
			diamonds: 20404,
			creatorPoints: 0,
			demons: {
				classic: {
					easy: 83,
					medium: 14,
					hard: 4,
					insane: 0,
					extreme: 0,
					total: 101,
				},
				platformer: {
					easy: 5,
					medium: 5,
					hard: 2,
					insane: 0,
					extreme: 0,
					total: 12,
				},
				weekly: 18,
				gauntlet: 20,
				total: 152,
				unique: 113,
			},
		},
		icons: {
			colors: {
				primary: 94,
				secondary: 3,
				glow: 3,
			},
			cube: 376,
			ship: 129,
			ball: 30,
			ufo: 83,
			wave: 26,
			robot: 34,
			hasGlow: true,
			spider: 29,
			deathEffect: 15,
			swing: 12,
			jetpack: 2,
		},
		social: {
			whoCanMessage: "all",
			whoCanFriend: "all",
			whoCanSeeComments: "friends",
			friendState: "none",
			registered: true,
		},
		connections: {
			youtube: "https://www.youtube.com/channel/UCT12Cnpkd-6kQEewKv_kqbQ",
			twitter: "https://twitter.com/Trigam04",
			twitch: "https://www.twitch.tv/TrigamDev",
		},
	}
	```

## **Trivia**
- Setting key `29` (Registered) to `0` prevents most aspects of the profile from loading
- Key `27` (Trail) is impossible to recieve from the server as the server doesn't store that information
