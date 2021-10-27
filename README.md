# Music_model_test

2ème application rails réalisée dans le cadre de la formation The Hacking Project

L'application se concentre toujours sur le backend et la création des models, class Album et Track, avec une base de données SQLite.

## QUESTION

a) Niveau facile

    Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
      ```Album.all.length = 347```

    Qui est l'auteur de la chanson "White Room" ?
      ```Track.where(title: "White Room")[0].artist
          => "Eric Clapton"
      ```

    Quelle chanson dure exactement 188133 milliseconds ?
      ```
        Track.where(duration: 188133)[0].title
         => "Perfect"
      ```

    Quel groupe a sorti l'album "Use Your Illusion II" ?
      ```
        Album.where(title: "Use Your Illusion II")[0].artist
        => "Guns N Roses"
      ```

b) Niveau Moyen

    Combien y a t'il d'albums dont le titre contient "Great" ?
        ```
            Album.where("title like ?", "%Great%").length
             => 13
        ```

    Supprime tous les albums dont le nom contient "music".
        ```

        ```

    Combien y a t'il d'albums écrits par AC/DC ?
    ```
        Album.where("title like ?", "%music%").each {|current| current.destroy}
    ```

    Combien de chanson durent exactement 158589 millisecondes ?
    ```
    Track.find_by duration: 158589
    => nil
    ```

c) Niveau Difficile

Pour ces questions, tu vas devoir effectuer des boucles dans la console Rails. C'est peu commun mais c'est faisable, tout comme dans IRB.

    puts en console tous les titres de AC/DC.
        ```
        Track.where(artist: "AC/DC").each {|current| puts current.title}
        ```

    puts en console tous les titres de l'album "Let There Be Rock".
        ```
        Track.where(album: "Let There Be Rock").each {|current| puts current.title}
        ```

    Calcule le prix total de cet album ainsi que sa durée totale.
        ```
        price_total = 0
        duration_total = 0
        Track.where(album: "Let There Be Rock").each {|current| price_total += current.price ; duration_total += current.duration }
        ```    
    Calcule le coût de l'intégralité de la discographie de "Deep Purple".
        ```
        price_total = 0
        Track.where(artist: "Deep Purple").each {|current| price_total += current.price }
        ```    

    Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
        ```
        Track.where(artist: "Eric Clapton").each {|current| current.artist = "Britney Spears" ; current.save }
        ```
