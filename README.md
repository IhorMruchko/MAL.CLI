# MAL.CLI
CLI tool for MyAnimeList service for anime tracking

## Installation

1. Run command below to verify that [`dotnet`](https://learn.microsoft.com/en-us/dotnet/core/install/) is installed
```console
dotnet --version
```
2. Install dotnet and execute
```console
dotnet tool install MyAnimeList.CLI --global
```
3. To connect MyAnimeList account to the CLI tool run the command:
```console
anime token
```
4. In the browser click "Allow".
> [!WARNING]
> First connection initialization could cause an issue. Please repeat steps 3 and 4.
6. Return to CLI and confirm anime list is displayed (if present in your account)

## Commands Overveiw

### List

* **_Definition_**
```console
anime list [--limit=10]
```
* **_Parameters_**:
  * _limit_
    * Optional
    * Default value = 10
    * Defines maximum amount of the anime to return. Returns specified value or all animes if their quantity less than [limit]

* **_Returns_**: all anime that are planed to be watched

* **_Examples_**

```console
anime list
```
> 1. Ao no Exorcist
> 2. Ao no Hako
> 3. Baccano!
> 4. Bastard!! Ankoku no Hakaishin: Jigoku no Chinkonka-hen
> 5. Cowboy Bebop
> 6. Darker than Black: Kuro no Keiyakusha
> 7. Dungeon ni Deai wo Motomeru no wa Machigatteiru Darou ka
> 8. Giji Harem
> 9. Gokusen
> 10. Hataage! Kemono Michi

```console
anime list --limit=5
```
> 1. Ao no Exorcist
> 2. Ao no Hako
> 3. Baccano!
> 4. Bastard!! Ankoku no Hakaishin: Jigoku no Chinkonka-hen
> 5. Cowboy Bebop

</br>

* **_Definition_**
```console
anime list watching
```
* **_Returns_**: List of all currently watching animes

* **_Examples_**
```console
anime list watching
```
> 1. Sword of the Demon Hunter: Kijin Gentosho - 21 / 24
> 2. Clevatess - 10 / 12
> 3. Scooped Up by an S-Rank Adventurer! - 9 / 12
> 4. New Saga - 9 / 12
> 5. Betrothed to My Sister's Ex - 8 / 12
> 6. The Water Magician - 8 / 12
> 7. Tougen Anki - 8 / 0
> 8. Apocalypse Bringer Mynoghra: World Conquest Starts with the Civilization of Ruin - 8 / 12
> 9. The Rising of the Shield Hero Season 4 - 8 / 12
> 10. Uglymug, Epicfighter - 8 / 12


### Find

* **_Definition_**
```console
anime find {searchString} [--limit=10]
```

* **_Parameters_**
  * searchString
    * Required
    * Search request / query for anime name
  * limit
    * Optional
    * Default value = 10
    * Defines maximum amount of the anime to return. Returns specified value or all animes if their quantity less than [limit]   

* **_Returns_** List of the anime fits search string with the [--limit] constrain

* **_Examples_**
```console
anime find "Atach Of Titan"
```

> 1 16498 - Shingeki no Kyojin \
> 2 25777 - Shingeki no Kyojin Season 2 \
> 3 31374 - Shingeki! Kyojin Chuugakkou \
> 4 35760 - Shingeki no Kyojin Season 3 \
> 5 38524 - Shingeki no Kyojin Season 3 Part 2 \
> 6 40028 - Shingeki no Kyojin: The Final Season \
> 7 23775 - Shingeki no Kyojin Movie 1: Guren no Yumiya \
> 8 36702 - Shingeki no Kyojin Season 2 Movie: Kakusei no Houkou \
> 9 23777 - Shingeki no Kyojin Movie 2: Jiyuu no Tsubasa \
> 10 18397 - Shingeki no Kyojin OVA

```console
anime find "JuJutsu Kaizen" --limit=1
```
> 1 40748 - Jujutsu Kaisen

### Plan

* **_Definition_**
```CLI
anime plan {animeID}
```

* **_Parameters_**
  * animeID
    * required
    * Anime id stored in the MyAnimeList database
    * Could be retrieved from `find` endpoint
   
* **_Returns_**: Confirmation of the anime added to your list

* **_Examples_**
```console
anime plan -1
```
> There is no anime

</br>

```console
anime plan 123
```
> Anime added to your list - Fushigi Yuugi

### Watch
* **_Definition_**
``` console
anime watch {animeId} [--eps]
```
* **_Parameters_**
  * animeId
    * Required
    * Anime id stored in the MyAnimeList database
    * Could be retrieved from `find` endpoint
  * eps
    * Optional
    * Default = 1
    * Number of watched episodes

* **_Returns_** Confirmation of the watched episodes

* **_Example_**
```console
anime watch 123
```
> You have watched  1 episodes of anime Fushigi Yuugi

</br>

```console
anime watch 123 --eps=5
```
> You have watched  5 episodes of anime Fushigi Yuugi

</br>

```
anime watch {animeName} [--eps]
```

## Issues
- [ ] First initialization causing issue with saving token
- [ ] Can not watch 1 episode of the anime when anime does not have number of all episodes.
