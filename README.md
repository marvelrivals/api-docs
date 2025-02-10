# MR(API) Documentation

Welcome to the official MR(API) by LunarAPI documentation for accessing Marvel Rivals Player Data, Game Data, and Hero Data!

## Table of Contents
- API
  - [Get All Acquirable Achievements](#get-all-acquirable-achievements)
  - [Get All Existing Gift Codes](#get-all-existing-gift-codes)
  - [Get All Heroes](#get-all-heroes)
  - [Get Hero by Name](#get-hero-by-name)
  - [Get Hero Statistics by Platform](#get-hero-statistics-by-platform)
  - [Get All Existing Items](#get-all-existing-items)
  - [Get Item by ID](#get-item-by-id)
  - [Get Leaderboards](#get-leaderboards)
  - [Get List of All Maps](#get-list-of-all-maps)
  - [Get Match by ID.](#get-a-match-by-its-id)
  - [Get Player Info by ID](#get-player-info-by-id)
  - [Get Player ID by Name](#get-player-id-by-name)
  - [Get Player Matches](#get-player-matches)
  - [Update a Player](#update-a-player)
  - [Get All Ranks](#get-all-ranks)
  - [Get All Hero Skins](#get-all-hero-skins)
  - [Get Skins for a Specific Hero](#get-skins-for-a-specific-hero) 
  - [Get Battlepass Info](#get-battlepass-info)
- [Response Format](#response-format)
- [Authentication & Rate Limiting](#authentication--rate-limiting)
- [License](#license)
- [Help](#help)
- [DISCLAIMER](#DISCLAIMER)
---

## Get All Acquirable Achievements
**Endpoint**:  
`GET /api/achievements`

**Description**:  
Retrieves a list of all acquirable achievements in the game.

**Parameters**:
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON array containing achievement details such as name, description, and rewards.

**Example**: 
```plaintext
GET /api/achievements?filter=name,points
```

---

## Get All Existing Gift Codes
**Endpoint**:  
`GET /api/codes`

**Description**:  
Fetches a list of all existing gift codes that can be redeemed in the game.

**Parameters**:
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON array containing gift code details, including code value, expiry date, and applicable rewards.

**Example**:  
```plaintext
GET /api/codes?filter=code
```

---

## Get All Heroes
**Endpoint**:  
`GET /api/heroes`

**Description**:  
Retrieves a list of all heroes with their complete details and statistics.

**Parameters**:
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON array containing hero details such as name, stats, abilities, and more.

**Example**:  
```plaintext
GET /api/heroes?filter=real_name,description
```

---

## Get Hero by Name
**Endpoint**:  
`GET /api/hero/:hero`

**Description**:  
Fetches detailed information about a specific hero by name.

**Parameters**:  
- [`hero`](types\heroes.md) (Path Parameter): The name of the hero (e.g., `Iron_Man`).
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON object containing detailed information about the hero, including stats, abilities, and skins.

**Example**:  
```plaintext
GET /api/hero/Iron_Man?filter=real_name,description
```

---

## Get Hero Statistics by Platform
**Endpoint**:  
`GET /api/heroes-stats/:platform`

**Description**:  
Fetches hero statistics based on the platform (PC or Console).

**Parameters**:  
- [`platform`](types\platforms.md) (Path Parameter): The platform to get hero stats for.
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON object containing hero statistics for the specified platform.

**Example**:
```plaintext
GET /api/heroes-stats/pc?filter=quickPlay.name,quickPlay.winRate,quickPlay.pickRate
```

---

## Get All Existing Items
**Endpoint**:  
`GET /api/items`

**Description**:  
Retrieves a list of all existing items in the game.

**Parameters**:
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON array containing item details, such as name, type, effect, and rarity.

**Example**:  
```plaintext
GET /api/items?filter=quality,type
```

---

## Get Item by ID

**Endpoint**:
`GET /api/item/:id`

**Description**:  
Retrieves an existing item in the game.

**Parameters**:  
- `id` (Path Parameter): The unique item ID (e.g., `30000001`).
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON object containing item details, such as name, type, effect, and rarity.

**Example**:  
```plaintext
GET /api/item/30000001?filter=quality,type
```

---

## Get Leaderboards
**Endpoint**:  
`GET /api/leaderboard/[:hero]`

**Description**:  
Fetches global or hero-specific leaderboards.

**Parameters**:  
- [`hero`](types\heroes.md) (Optional Path Parameter): The name of a specific hero to fetch the leaderboard for (e.g., `captain-america`).
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)
- [`platform`](types\platforms.md) (Query Parameter): The platform to get hero stats for.

**Response**:  
A JSON object containing leaderboard data. If a hero name is provided, it returns the leaderboard for that hero.

**Hero Leaderboard Example**:  
```plaintext
GET /api/leaderboard/captain-america?filter=rank,score,player_id&platform=xbox
```

**Global Leaderboard Example**
```plaintext 
GET /api/leaderboard?filter=rank,score,player_id&platform=playstation
```

---

## Get List of All Maps
**Endpoint**:
`GET /api/maps`

**Description**:
Retrieves a list of all the maps in the game.

**Parameters**:
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:
A JSON array containing map details, such as name, description, and gamemode.

**Example**:
```plaintext
GET /api/maps?filter=name,gamemode
```

---

## Get a Match by it's ID.
**Endpoint**:
`GET /api/match/:id`

**Description**:
Get a match by it's id.

**Parameters**:  
- `id` (Path Parameter): The unique match ID (e.g., `6711732_1738013791_802_11001_50`).
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:
A JSON object containing the MVP, SVP, gamemode, and players with their statistics.

**Example**:
```plaintext
GET /api/match/6711732_1738013791_802_11001_50?filter=replay_id,mvp,svp
```

---

## Get Player Info by ID
**Endpoint**:  
`GET /api/player/:id`

**Description**:  
Fetches detailed information about a player using their unique ID.

**Parameters**:  
- `id` (Path Parameter): The unique player ID (e.g., `1695483110`).
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON object containing player details, such as stats, achievements, and rank.

**Example**:  
```plaintext
GET /api/player/1695483110?filter=player_name,player_uid,stats
```

---

## Get Player ID by Name
**Endpoint**:  
`GET /api/player-id/:name`

**Description**:  
Retrieves a player’s unique ID based on their username.

**Parameters**:  
- `name` (Path Parameter): The player's username (e.g., `Toxic`).
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON object containing the player's unique ID.

**Example**:  
```plaintext
GET /api/player-id/Toxic?filter=id
```

---

## Get Player Matches

**Endpoint**:
`GET /api/player-match/:id`

**Description**:
Gets all the player's previous matches.

**Parameters**:  
- `id` (Path Parameter): The unique player ID (e.g., `1695483110`).
- `page` (Query Parameter): Use this to see more matches
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:
A JSON array containing the match UID, gamemode, player's statistics, and score.

**Example**
```plaintext
GET api/player-match/1695483110?page=2&filter=match_uid,match_timestamp
```

---

## Update a Player

**Endpoint**:
`GET /api/player-update/:id`

**Description**:
Fetches the latest changes for a specific player.

> **NOTE**: This will take a few minutes to update.

**Parameters**:  
- `id` (Path Parameter): The unique player ID (e.g., `1695483110`).
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:
A JSON object containing if the operation was successful.

**Example**:
```plaintext
GET /api/player-update/1695483110?filter=success
```


---


## Get All Ranks
**Endpoint**:  
`GET /api/ranks`

**Description**:  
Fetches information about all available ranks and their player totals.

**Parameters**:
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON array containing rank details, including rank name, total players, and associated rewards.

**Example**:  
```plaintext
GET /api/ranks?filter=celestial.3
```

---

## Get All Hero Skins
**Endpoint**:  
`GET /api/skins`

**Description**:  
Retrieves a list of all available hero skins and variations.

**Parameters**:
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON array containing skin details such as skin name, type, and variations.

**Example**:  
```plaintext
GET /api/skins?filter=name,quality
```

---

## Get Skins for a Specific Hero
**Endpoint**:  
`GET /api/skin/:hero`

**Description**:  
Fetches all skins for a specific hero.

**Parameters**:  
- [`hero`](types\heroes.md) (Path Parameter): The name of the hero whose skins are requested (e.g., `iron_man`).
- `filter` (Query Parameter): Lets you choose which results to include. (e.g. `id`, `name`)

**Response**:  
A JSON array containing all skins for the specified hero.

**Example**:  
```plaintext
GET /api/skin/iron_man?filter=name,quality
```

---

## Get Battlepass Info

**Endpoint**:
`GET /api/battlepass`

**Description**:
Fetches season's battlepass content

**Parameters**:
- `season` (Optional Query Parameter) Choose the season you want. (e.g. `0` or `1`) By default it will grab the latest season.

**Response**:
A JSON object containing the `start_time`, `end_time`, a JSON array with the pages and their contents.

**Example**:
```plaintext
GET /api/battlepass?season=0
```

---

## Response Format
- All endpoints return data in **JSON** format.
- Typical response objects contain arrays or objects with attributes like `name`, `description`, `id`, etc., depending on the endpoint.

<details>
<summary><b>Example Response for Hero by Name:</b></summary>

```json
{
  "id": "1034",
  "name": "Iron Man",
  "real_name": "Anthony \"tony\" Stark",
  "transformations": [
    {
      "id": 0,
      "icon": "https://mrapi.org/assets/characters/iron-man-headbig-0.png",
      "name": "Iron Man",
      "health": "250",
      "movement_speed": "6 m/s"
    }
  ],
  "en_name": "Iron Man",
  "description": "Armed with superior intellect and a nanotech battlesuit of his own design, Tony Stark stands alongside gods as the Invincible Iron Man. His state of the art armor turns any battlefield into his personal playground, allowing him to steal the spotlight he so desperately desires.",
  "slug": "iron-man",
  "team": "[\"Avengers\"]",
  "difficulty": "2",
  "attack_type": "Projectile Heroes",
  "role": "DUELIST",
  "image_square": "https://mrapi.org/assets/characters/iron-man-square.png",
  "image_transverse": "https://mrapi.org/assets/characters/iron-man-transverse.png",
  "icon": "https://mrapi.org/assets/characters/iron-man-headbig.png",
  "image": "https://mrapi.org/assets/characters/iron-man-portrait.png",
  "logo_small": "https://mrapi.org/assets/characters/iron-man-logo.png",
  "logo": "https://mrapi.org/assets/characters/iron-man-logo-small.png",
  "skins": [
    "1034001",
    "1034100",
    "1034501",
    "1034800",
    "1034300"
  ],
  "abilities": [
    {
      "id": 103411,
      "icon": "https://mrapi.org/assets/abilities/103411.png",
      "name": "Repulsor Blast",
      "type": "Weapon",
      "isCollab": false,
      "description": "Fire nano pulse cannons forward.",
      "additional_fields": {
        "Key": "Left Click",
        "Ammo": "100",
        "Range": "5m spherical radius",
        "Damage": "65",
        "Casting": "Straight-line projectile that generates a spell field upon impact",
        "Fire Rate": "1.39 rounds per second",
        "Critical Hit": "No",
        "Ammo Consumption": "16 damage per round",
        "Projectile Speed": "80 m/s",
        "Special Mechanic 1": "After firing the one-handed repulsor twice in a row, the next attack will fire two repulsors at once",
        "Special Mechanic 2": "Repulsor Blast and Unibeam share the same ammo count",
        "Spell Field Damage": "40",
        "Two-handed Repulsors": " ",
        "Spell Field Damage Falloff": "40% falloff at 5m"
      },
      "transformation_id": 0
    },
    {
      "id": 103421,
      "icon": "https://mrapi.org/assets/abilities/103421.png",
      "name": "Unibeam",
      "type": "Weapon",
      "isCollab": false,
      "description": "Fire a unibeam forward.",
      "additional_fields": {
        "Key": "Right Click",
        "Ammo": "100",
        "Damage": "120 damage per second",
        "Casting": "Channeled",
        "Beam Length": "25m",
        "Critical Hit": "No",
        "Ammo Consumption": "10/s",
        "Special Mechanic": "Repulsor Blast and Unibeam share the same ammo count"
      },
      "transformation_id": 0
    },
    {
      "id": 103431,
      "icon": "https://mrapi.org/assets/abilities/103431.png",
      "name": "Hyper-velocity",
      "type": "Normal",
      "isCollab": false,
      "description": "Activate \u003COrange\u003EHyper-Velocity\u003C/\u003E state for swift forward flight.",
      "additional_fields": {
        "Key": "SHIFT",
        "Energy Cost": "15/s",
        "Maximum Energy": "120",
        "Movement Boost": "100%",
        "Energy Recovery Speed": "10/s"
      },
      "transformation_id": 0
    },
    {
      "id": 103441,
      "icon": "https://mrapi.org/assets/abilities/103441.png",
      "name": "Micro-missile Barrage",
      "type": "Normal",
      "isCollab": false,
      "description": "When \u003COrange\u003EHyper-Velocity\u003C/\u003E or \u003COrange\u003EArmor Overdrive\u003C/\u003E is used, Iron Man can launch a missile bombardment.",
      "additional_fields": {
        "Key": "F",
        "Range": "2m spherical radius",
        "Casting": "Scatter-type projectile that generates a spell area upon impact",
        "Cooldown": "8s",
        "Missiles": "16",
        "Projectile Speed": "15 m/s",
        "Special Mechanic": "Launch missiles directly beneath Iron Man",
        "Spell Field Damage": "20 damage per round"
      },
      "transformation_id": 0
    },
    {
      "id": 103451,
      "icon": "https://mrapi.org/assets/abilities/103451.png",
      "name": "Armor Overdrive",
      "type": "Normal",
      "isCollab": false,
      "description": "Activate \u003COrange\u003EArmor Overdrive\u003C/\u003E state, enhancing damage of \u003COrange\u003ERepulsor Blast\u003C/\u003E and \u003COrange\u003EUnibeam\u003C/\u003E.",
      "additional_fields": {
        "Key": "E",
        "Cooldown": "20s",
        "Duration": "10s"
      },
      "transformation_id": 0
    },
    {
      "id": 103461,
      "icon": "https://mrapi.org/assets/abilities/103461.png",
      "name": "Invincible Pulse Cannon",
      "type": "Ultimate",
      "isCollab": false,
      "description": "Fire a devastating pulse cannon in the targeted direction, delivering catastrophic damage to the targeted area upon impact.",
      "additional_fields": {
        "Key": "Q",
        "Casting": "Straight-line projectile that generates a spell field upon impact",
        "Energy Cost": "2800",
        "Explosion Range": "10m spherical radius",
        "Damage Over Time": "300/s",
        "Explosion Damage": "1000",
        "Projectile Speed": "25 m/s",
        "Special Mechanic": "As the projectile travels, it creates a dispersive spell field that deals Damage Over Time to nearby enemies",
        "Dispersive Spell Field": "Length: 15m, Width: 5m, Height: 5m",
        "Spell Field Damage Falloff": "5% falloff at 10m"
      },
      "transformation_id": 0
    },
    {
      "id": 103454,
      "icon": "https://mrapi.org/assets/abilities/103454.png",
      "type": "Normal",
      "isCollab": true,
      "additional_fields": {
        "Health": "250",
        "Movement Mode": "Flight",
        "Movement Speed": "6 m/s"
      },
      "transformation_id": 0
    }
  ],
  "meta": [
    {
      "platform": "pc",
      "mode": "quickplay",
      "rank": "all",
      "appearance_rate": "7.69",
      "win_rate": "49.06"
    },
    {
      "platform": "pc",
      "mode": "competitive",
      "rank": "all",
      "appearance_rate": "5.92",
      "win_rate": "49.38"
    },
    {
      "platform": "pc",
      "mode": "competitive",
      "rank": "bronze",
      "appearance_rate": "6.62",
      "win_rate": "48.04"
    },
    {
      "platform": "pc",
      "mode": "competitive",
      "rank": "diamond",
      "appearance_rate": "6.08",
      "win_rate": "52.81"
    },
    {
      "platform": "pc",
      "mode": "competitive",
      "rank": "gold",
      "appearance_rate": "5.26",
      "win_rate": "50.38"
    },
    {
      "platform": "pc",
      "mode": "competitive",
      "rank": "grandmaster and above",
      "appearance_rate": "6.69",
      "win_rate": "52.70"
    },
    {
      "platform": "pc",
      "mode": "competitive",
      "rank": "platinum",
      "appearance_rate": "5.16",
      "win_rate": "51.51"
    },
    {
      "platform": "pc",
      "mode": "competitive",
      "rank": "silver",
      "appearance_rate": "5.68",
      "win_rate": "49.29"
    },
    {
      "platform": "console",
      "mode": "quickplay",
      "rank": "all",
      "appearance_rate": "7.69",
      "win_rate": "49.06"
    },
    {
      "platform": "console",
      "mode": "competitive",
      "rank": "all",
      "appearance_rate": "7.19",
      "win_rate": "49.25"
    },
    {
      "platform": "console",
      "mode": "competitive",
      "rank": "bronze",
      "appearance_rate": "8.05",
      "win_rate": "48.29"
    },
    {
      "platform": "console",
      "mode": "competitive",
      "rank": "diamond",
      "appearance_rate": "6.30",
      "win_rate": "52.63"
    },
    {
      "platform": "console",
      "mode": "competitive",
      "rank": "gold",
      "appearance_rate": "6.46",
      "win_rate": "49.79"
    },
    {
      "platform": "console",
      "mode": "competitive",
      "rank": "grandmaster and above",
      "appearance_rate": "6.38",
      "win_rate": "53.56"
    },
    {
      "platform": "console",
      "mode": "competitive",
      "rank": "platinum",
      "appearance_rate": "6.12",
      "win_rate": "51.13"
    },
    {
      "platform": "console",
      "mode": "competitive",
      "rank": "silver",
      "appearance_rate": "7.20",
      "win_rate": "48.95"
    }
  ]
}
```
</details>

---

## Authentication & Rate Limiting
- **Authentication**: This API does not require authentication.
- **Rate Limiting**: Be mindful of any rate limiting imposed by the server. To avoid making too many requests in a short time, refer to the API’s rate limits and ensure your requests are spaced out appropriately.

---

## License

This API is made available under the **MIT License**. See [LICENSE](LICENSE) for details.

---

Feel free to submit any issues or suggestions via the [Issues page](https://github.com/marvelrivals/issues).

## Help

Please join our [Discord](https://discord.gg/3kSsWEZpft) for help! 


## DISCLAIMER
> This API is NOT official and NOT endorsed by Marvel Rivals or NetEase in any way. All names, resources and generally any Marvel Rivals related content belongs to Marvel Rivals and NetEase.

