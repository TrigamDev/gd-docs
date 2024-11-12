# **Server User Resource**
## **User**
Each player of Geometry Dash has a profile containing various types of data, such as info, stats, completed levels, icons, and connected socials.

A typical user server response is structured with a `key:value:key:value` pairing.

!!! example
	```
	1:RobTop:2:16:13:20:17:175:10:35:11:2:51:0:3:2966:52:180:46:3259:4:5:8:0:18:2:19:1:50:0:20:UCz_yk8mDSAnxJq0ar66L4sw:21:483:22:1:23:1:24:1:25:1:26:1:28:0:43:1:48:1:53:1:54:1:30:258348:16:71:31:0:44:RobTopGames:45:robtopgames:49:2:55:2,2,1,0,0,0,0,0,0,0,0,0:56:51,32,82,280,105,20,71,5:57:0,3,6,21,6,2,0:29:1
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
	2,2,1,0,0,0,0,0,0,0,0,0
	```

#### **Level List**
A user's level list contains all of the classic levels the user has completed.  
From left to right, it is in the order of:

- Auto, Easy, Normal, Hard, Harder, Insane, Daily, Gauntlet

!!! example
	```md
	51,32,82,280,105,20,71,5
	```

#### **Platformer Level List**
A user's platformer level list contains all of the platformer levels the user has completed.  
From left to right, it is in the order of:

- Auto, Easy, Normal, Hard, Harder, Insane

!!! example
	```md
	0,3,6,21,6,2,0
	```

## **Parsed User Example**
???+ example
	```json
	{
		info: {
			username: "RobTop",
			userId: 16,
			globalRank: 258348,
			accountId: 71,
			modLevel: "elder_mod"
		},
		stats: {
			levels: {
				classic: {
					auto: 51,
					easy: 32,
					normal: 82,
					hard: 280,
					harder: 105,
					insane: 20,
					daily: 71,
					gauntlet: 5,
					total: 646,
					unique: 570
				},
				platformer: {
					auto: 0,
					easy: 3,
					normal: 6,
					hard: 21,
					harder: 6,
					insane: 2,
					total: 38,
					unique: 38
				},
				total: 684,
				unique: 608
			},
			secretCoins: 20,
			userCoins: 175,
			stars: 2966,
			moons: 180,
			diamonds: 3259,
			creatorPoints: 0,
			demons: {
				classic: {
					easy: 2,
					medium: 2,
					hard: 1,
					insane: 0,
					extreme: 0,
					total: 5
				},
				platformer: {
					easy: 0,
					medium: 0,
					hard: 0,
					insane: 0,
					extreme: 0,
					total: 0
				},
				weekly: 0,
				gauntlet: 0,
				total: 5,
				unique: 5
			}
		},
		icons: {
			colors: {
				primary: 35,
				secondary: 2,
				glow: 0
			},
			cube: 483,
			ship: 1,
			ball: 1,
			ufo: 1,
			wave: 1,
			robot: 1,
			hasGlow: false,
			spider: 1,
			deathEffect: 1,
			swing: 1,
			jetpack: 1
		},
		social: {
			whoCanMessage: "none",
			whoCanFriend: "none",
			whoCanSeeComments: "all",
			friendState: "none",
			registered: true
		},
		connections: {
			youtube: "https://www.youtube.com/channel/UCz_yk8mDSAnxJq0ar66L4sw",
			twitter: "https://twitter.com/RobTopGames",
			twitch: "https://www.twitch.tv/robtopgames"
		}
	}
	```

## **Trivia**
- Setting key `29` (Registered) to `0` prevents most aspects of the profile from loading
- Key `27` (Trail) is impossible to recieve from the server as the server doesn't store that information
