## Explanation and Notes for Your Project
### 2022-05-06
1. Missing axios, Please install it
2. List must be Array unless you know what's going on
3. Recommended to change your method "mounted" to "loadData". mounted is a vue keyboard. You can still use the "mounted" inside method. It is very easy to make mix up the all the things
4. Modify to "create: function".  
   From
   ```javascript
    created: function() {
        this.mounted();
    },
   ```  
   To
   ```javascript
   mounted() {
        this.loadData()
   },
   ```
5. Inside Vue, it doesn't necessary to use ";" at the end of the line
6. If you don't understand the key meaning, you should have to study the movie data first. I have quoted the example below.  
   ```json
   {
    "page": 1,
    "results": [
        {
            "poster_path": null,
            "adult": false,
            "overview": "Go behind the scenes during One Directions sell out \"Take Me Home\" tour and experience life on the road.",
            "release_date": "2013-08-30",
            "genre_ids": [
                99,
                10402
            ],
            "id": 164558,
            "original_title": "One Direction: This Is Us",
            "original_language": "en",
            "title": "One Direction: This Is Us",
            "backdrop_path": null,
            "popularity": 1.166982,
            "vote_count": 55,
            "video": false,
            "vote_average": 8.45
        },
        {
            "poster_path": null,
            "adult": false,
            "overview": "",
            "release_date": "1954-06-22",
            "genre_ids": [
                80,
                18
            ],
            "id": 654,
            "original_title": "On the Waterfront",
            "original_language": "en",
            "title": "On the Waterfront",
            "backdrop_path": null,
            "popularity": 1.07031,
            "vote_count": 51,
            "video": false,
            "vote_average": 8.19
        }
    ]}
   ```
   1. First, download the movies.json under data into your company. Open FireFox, File -> Open , Choose movies.json.  
   2. Then you got a "Tree" like data structure. The First Level have "page" and "results"
   3. "page" , it should be page number
   4. "results", it is the movies list
   5. In the "results" array, we got lots of data, For each movie, we got "id" field. It is the identifier ( we call id / key ) to represent this movie.
   6. Then put
   ```
      :key="movie.id" 
   ```
   7. this is what we call "key"