# MAL.CLI
CLI tool for MyAnimeList service for anime tracking

## Installation

1. Run command below to verify that [`dotnet`](https://learn.microsoft.com/en-us/dotnet/core/install/) is installed
```console
dotnet --version
```
2. Add new source to dontet (optional, but recommended)
```console
dotnet nuget add source --username USERNAME --password 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 --store-password-in-clear-text --name github "https://nuget.pkg.github.com/MAL.CL/index.json" 
```
> [!NOTE]
> Replace USERNAME with your account. Value could be retrieved from URL
3. Install dotnet and execute
```console
dotnet tool install MyAnimeList.CLI --global
```
4. To connect MyAnimeList account to the CLI tool run the command:
```console
anime token
```
5. In the browser click "Allow".
> [!WARNING]
> First connection initialization could cause an issue. Please repeat steps 3 and 4.
6. Return to CLI and confirm anime list is displayed (if present in your account)

## Commands Overveiw

<details>
 <summary>List</summary>

 </br>
 
 ```console
  anime list <watching> [--limit=10]
 ```

* **_Parameters_**:
  * _limit_
    * Optional
    * Default value = 10
    * Defines maximum amount of the anime to return. Returns specified value or all animes if their quantity less than [limit]
  * _watching_
    * Optional
    * Defines if watching anime will be listed
  
**_Returns_**: all anime that are planed to be watched
  
**_Examples_**
 <details>
  <summary>Example 1</summary>

   </br>
  
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
      
</details>
      
   <details>
    <summary>Example 2</summary>

   </br>
   
   ```console
    anime list --limit=5
   ```
   > 1. Ao no Exorcist
   > 2. Ao no Hako
   > 3. Baccano!
   > 4. Bastard!! Ankoku no Hakaishin: Jigoku no Chinkonka-hen
   > 5. Cowboy Bebop
   </details>

  <details>
   <summary>Example 3</summary>

   </br>
   
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
   
  </details>
</details>

<details>
 <summary>Find</summary>

  </br>

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

 **_Returns_** List of the anime fits search string with the [--limit] constrain

 **_Examples_**

 <details>
  <summary>Example 1</summary>

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

 </details>

 <details>
  <summary>Example 2</summary>

  ```console
   anime find "JuJutsu Kaizen" --limit=1
  ```
  > 1 40748 - Jujutsu Kaisen

 </details>
 
</details>

<details>
 <summary>Plan</summary>

 </br>
 
 ```console
  anime plan {animeID}
 ```

 * **_Parameters_**
   * animeID
     * required
     * Anime id stored in the MyAnimeList database
     * Could be retrieved from `find` endpoint
   
 **_Returns_**: Confirmation of the anime added to your list

 **_Examples_**

 <details>
  <summary>Example 1</summary>

  </br>

  ```console
   anime plan -1
  ```

  > There is no anime
 </details>

 <details>
  <summary>Example 2</summary>

  </br>

  ```console
   anime plan 123
  ```
  > Anime added to your list - Fushigi Yuugi

 </details>
 
</details>


<details>
 <summary>Watch</summary>

 </br>
 
 ``` console
  anime watch {animeId|animeName} [--eps]
 ```

  * **_Parameters_**
    * animeId
      * Required
      * Anime id stored in the MyAnimeList database
      * Could be retrieved from `find` endpoint
    * animeName
      * Required
      * Anime name phrase from MyAnimeList database
    * eps
      * Optional
      * Default = 1
      * Number of watched episodes
     
 **_Returns_**: Confirmation of the watched episodes

 **_Example_**

 <details>
  <summary>Example 1</summary>

  </br>
  
  ```console
   anime watch 123
  ```
  > You have watched  1 episodes of anime Fushigi Yuugi
 </details>

 <details>
  <summary>Example 2</summary>

  </br>

  ```console
  anime watch 123 --eps=5
  ```
  > You have watched  5 episodes of anime Fushigi Yuugi
 </details>
</details>

<details>
 <summary>Rate</summary>

 </br>

 ```console
 anime rate {animeID|animeName} {score} [completed] [limit=10]
 ```
 * **_Parameters_**
   * animeID
     * Required
      * Anime id stored in the MyAnimeList database
      * Could be retrieved from `find` endpoint
    * animeName
      * Required
      * Anime name phrase from MyAnimeList database
   * score
     * score to rate the anime
   * completed
     * defines if anime will be marked as completed. Watching status by default is set for rated anime
   * limit
     * Optional
     * Used when [animeName] is provided
     * Default value = 10
     * Defines maximum amount of the anime to return. Returns specified value or all animes if their quantity less than [limit]
 
 * **_Returns_**:
   * Anime not selected - if anime is not selected from list if animeName is provided
   * Anime not found - if anime is not present in the database
   * Rate is aborted - if anime already has rate and confirmation is not passed
   * Rate was updated for anime - if anime was rated

 Examples

 <details>
  <summary>Example 1</summary>

  </br>
  
  ```console
  anime rate 123 5
  ```
  > Rate was updated for anime - Fushigi Yuugi
  
 </details>

 <details>
  <summary>Example 2</summary>

  </br>

  ```console
  anime rate 123 9
  ```
  > Anime is already rated (5), would you like to update it?y </br>
  > Rate was updated for anime - Fushigi Yuugi
 </details>

 <details>
  <summary>Example 3</summary>

  </br>

  ```console
  anime rate "Fushigi Yuugi" 7
  ```
  > 1. Fushigi Yuugi
  > 2. Fushigi Yuugi: Dai Ni Bu
  > 3. Fushigi Yuugi: Eikouden
  > 4. Fushigi Yuugi OVA
  > 5. Fushigi Yuugi Special: Nakago Shikkari Shinasai!
  > 6. Fushigi na Somera-chan
  > 7. Fushigi no Umi no Nadia
  > 8. Nils no Fushigi na Tabi
  > 9. Mushishi
  > 10. Fushigi na Melmo

  1
  > Anime is already rated (9), would you like to update it?y </br>
  > Rate was updated for anime - Fushigi Yuugi
 </details>

 <details>
  <summary>Example 4</summary>

  </br>

  ```console
  anime rate "Fushigi Yuugi" 8 --limit=5
  ```
  > 1. Fushigi Yuugi
  > 2. Fushigi Yuugi: Dai Ni Bu
  > 3. Fushigi Yuugi: Eikouden
  > 4. Fushigi Yuugi OVA
  > 5. Fushigi Yuugi Special: Nakago Shikkari Shinasai!

  1
  > Anime is already rated (7), would you like to update it?y </br>
  > Rate was updated for anime - Fushigi Yuugi
 </details>

 <details>
  <summary>Example 5</summary>

  </br>

  ```console
  anime rate "Fushigi Yuugi" 8 --limit=5
  ```
  > 1. Fushigi Yuugi
  > 2. Fushigi Yuugi: Dai Ni Bu
  > 3. Fushigi Yuugi: Eikouden
  > 4. Fushigi Yuugi OVA
  > 5. Fushigi Yuugi Special: Nakago Shikkari Shinasai!

  10
  > Anime not selected
 </details>

 <details>
  <summary>Example 6</summary>

  </br>

  ```console
  anime rate "Fushigi Yuugi" 8 --limit=5
  ```
  > 1. Fushigi Yuugi
  > 2. Fushigi Yuugi: Dai Ni Bu
  > 3. Fushigi Yuugi: Eikouden
  > 4. Fushigi Yuugi OVA
  > 5. Fushigi Yuugi Special: Nakago Shikkari Shinasai!

  1
  > Anime is already rated (7), would you like to update it?n </br>
  > Rate is aborted
 </details>
</details>

## Upcoming Features
- [ ] [Progress of anime watching](https://github.com/IhorMruchko/MAL.CLI/issues/3)

## Issues
- [ ] [#1] First initialization causing issue with saving token
- [ ] [#2] Can not watch 1 episode of the anime when anime does not have number of all episodes.


[#1]: https://github.com/IhorMruchko/MAL.CLI/issues/1
[#2]: https://github.com/IhorMruchko/MAL.CLI/issues/2 
