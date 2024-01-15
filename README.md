# PokeMMO Data
PokeMMO game data formatted to json for easy use in [PokeMMOHub](https://pokemmohub.com) and other projects.

This repository is meant to live from User contributions. If you have any data you would like to contribute or see any outdated data, please submit a pull request or issue. Please see the [Contributing](#contributing) section for more information.

### Disclaimer
This repository is not affiliated with PokeMMO in any way. This repository is maintained by [PokeMMOHub](https://pokemmohub.com). You can reach us on [Discord](https://discord.gg/F54ggpgUMj).

# Table of Contents
- [PokeMMO Data](#pokemmo-data)
    - [Disclaimer](#disclaimer)
- [Table of Contents](#table-of-contents)
- [Project Structure](#project-structure)
  - [Data](#data)
    - [Items](#items)
      - [`items.json`](#itemsjson)
      - [`items-berry.json`](#items-berryjson)
      - [`items-cosmetic.json`](#items-cosmeticjson)
    - [Monsters](#monsters)
      - [`monsters.json`](#monstersjson)
      - [`moves.json`](#movesjson)
      - [`pokedex.json`](#pokedexjson)
  - [Assets](#assets)
    - [Items](#items-1)
      - [`itemsicons`](#itemsicons)
  - [Locales](#locales)
- [Contributing](#contributing)
  - [Pull Request Guidelines](#pull-request-guidelines)
- [Restrictions](#restrictions)

# Project Structure
The project is split up into 3 main folders: `data`, `assets` and `locales`.

## Data
The `data` folder contains all the data for the game. We currently have data for the following categories:
- Items 
- Monsters
- Moves

### Items
The way that PokeMMO Items work is that we have either og items or custom items. Og items are dumped from the roms and custom items are hardcoded into the game. since we have multiple regions, multiple roms and bc of poor cooding decisions, we have multiple item ids for the same item. This is why we dont just have one `items.json` file with all the item data but seperate items into types which can hold general information and backlinks to the actual items in the game.

#### `items.json`
This file holds all the items in the game. It contains the internal item id, its type, it's english name and description. The name and description are base for any translation. 

The data is structured as follows:
```json
[
    ...
    {
        "id": 1,
        "type": 2,
        "name": "Master Ball",
        "description": "The best BALL with the ultimate\nperformance. It will catch any wild\nPOKéMON without fail."
    },
    ...
]
```

**_NOTE:_** This data can be dumped from the games memory. Dumping this data is not supported by the Client and is not recommended since it is against the PokeMMO ToS.

#### `items-berry.json`
This file holds all the berry items in the game. It contains important information such as the berry's growth time and the berry's type. Berries should have their own ids and backlink to every actual item in the game.

The data is structured as follows:
```json
[
    ...
    {
        "bitter_degree": 0,
        "dry_degree": 0,
        "first_water_time": 3,
        "grow_time": 16,
        "max_harvest": 6,
        "min_harvest": 3,
        "nature_power_power": 80,
        "nature_power_type": 10,
        "other_water_time": 2,
        "reduce_time": 2,
        "sour_degree": 0,
        "spicy_degree": 3,
        "sweet_degree": 0,
        "wither_time": 8,
        "items": [
            133,
            1133,
            5149,
            6149,
            8149,
            9149
        ],
        "id": 1
    },
    ...
]
```

**_NOTE:_** This data needs to be manually updated when new berries are added to the game or when certain values change.

#### `items-cosmetic.json`
This file holds data about certain cosmetic items. These cosmetics are not actual items in the roms but are hardcoded into the game. This file is used to display the correct information about these items. `item_id` here is a list if ids since there can be multiple items for the same cosmetic.

The data is structured as follows:
```json
[
    ...
    {
        "attribute": 0,
        "festival": 3,
        "limitation": 1,
        "month": 12,
        "slot": 2,
        "year": 2013,
        "item_id": [
            2320
        ]
    },
    ...
]
```

**_NOTE:_** This data needs to be manually updated when new cosmetics are added to the game or when certain values change.

### Monsters
Monsters are Pokemon but since the game itself calls them monster we will call them monster as well. The data for monsters is split up into 3 files: `monsters.json`, `moves.json` and `pokedex.json`.

#### `monsters.json`
This file holds all the monsters in the game. It contains the internal monster id, pokedex data and it's english name. The name is used for any translation.

We won't provide an example here since the file is too big. Please check the file itself for more information.

**_NOTE:_** This data can be dumped from the games memory. Dumping this data is supported by the Client via the dump moddable resources option in the settings.

#### `moves.json`
This file holds all the moves in the game. It contains the internal move id, it's english name and description. The name and description are base for any translation.

The data is structured as follows:
```json
[
    ...
    {
        "id": 1,
        "name": "Pound",
        "skill_damage_type": "PHYSICAL",
        "base_power": 40,
        "base_accuracy": 100,
        "base_pp": 35,
        "priority": 0,
        "type": "NORMAL",
        "target_type": 0,
        "true_damage": false
    },
    ...
]
```

**_NOTE:_** This data can be dumped from the games memory. Dumping this data is supported by the Client via the dump moddable resources option in the settings.

#### `pokedex.json`
This file links monsters to their spot in the pokedex. It contains the internal monster id and the pokedex number. We start to count at 1 for the first monster. 

The data is structured as follows:
```json
[
    ...
    {
        "id": 1,
        "kanto": 1,
        "hoenn": 0,
        "unova": 0,
        "sinnoh": 0,
        "johto": 0
    },
    ...
]
```

**_NOTE:_** This data needs to be manually updated when new monsters are added to the game or when certain values change.

## Assets
The `assets` folder contains all the assets for the game. We currently have assets for the following categories:
- Items

### Items

#### `itemsicons`
This folder contains all the item icons for the game. The icons are named after their internal item id. The icons are in `.png` format.

**_NOTE:_** This data can be dumped from the games memory. Dumping this data is supported by the Client via the dump moddable resources option in the settings.

## Locales
The `locales` folder contains all the translations for the game. We currently have translations for the following categories:
- Items
- Monsters
- locations
  
These files contains the english name/description in lowercase mapped to the target language.

**_NOTE:_** This data is a mix of manually translated data and data dumped from the games memory. Either way, dumping this data is not supported by the Client and is not recommended since it is against the PokeMMO ToS. 

# Contributing
If you would like to contribute to this project, please follow the steps below:

1. Fork this repository
2. Make your changes
3. Submit a pull request
4. Wait for your pull request to be reviewed

## Pull Request Guidelines
- Please make sure that your pull request is not a duplicate of an existing pull request
- Please make sure your pull request mentions the issue it is fixing
- Please make sure your pull request is not breaking anything
- Please make sure to follow the project structure

# Restrictions
- If you use this data in your project, please make sure to credit this repository
- If you update this data or add more information, please create a pull request so everyone can benefit from it