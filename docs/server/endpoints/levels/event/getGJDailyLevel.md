# **getGJDailyLevel.php**
`https://www.boomlings.com/database/getGJDailyLevel.php`

Gets the index of the current daily level and the time left (in seconds).

## **Parameters**
| Name | Value | Type | Required? | Description |
|------|-------|------|-----------|-------------|
| secret | Wmfd2893gb7 | **String** | **✔** | A 'password' needed for all API requests. |
| weekly | 0 | **Integer** | ✖ | Whether to get the daily or weekly level. (`0`: Daily, `1`: Weekly) |
| gameVersion | 22 | **Integer** | ✖ | The version of Geometry Dash. |
| binaryVersion | 42 | **Integer** | ✖ | The version of the Geometry Dash servers. |
| gdw | 0 | **Integer** | ✖ | Whether the request is being made from Geometry Dash World. |
| accountID | - | **Integer** | ✖ | The account ID of the user making the request. |
| uuid | - | **Integer** | ✖ | The user ID of the user making the request. |
| udid | - | **String** | ✖ | The [UDID](../../../../topics/encoding/udid) |
| gjp2 | - | **GJP2** | ✖ | The GJP2 of the user making the request. |