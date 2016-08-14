# freeCodeCamp-Record-Collection

You are given a JSON object representing a part of your musical album collection. Each album has several properties and a unique id number as its key. Not all albums have complete information.

Write a function which takes an album's id (like 2548), a property prop (like "artist" or "tracks"), and a value (like "Addicted to Love") to modify the data in this collection.

If prop isn't "tracks" and value isn't empty (""), update or set the value for that record album's property.

Your function must always return the entire collection object.

There are several rules for handling incomplete data:

If prop is "tracks" but the album doesn't have a "tracks" property, create an empty array before adding the new value to the album's corresponding property.

If prop is "tracks" and value isn't empty (""), push the value onto the end of the album's existing tracks array.

If value is empty (""), delete the given prop property from the album.


    var collection = {
    "2548": {
      "album": "Slippery When Wet",
      "artist": "Bon Jovi",
      "tracks": [ 
        "Let It Rock", 
        "You Give Love a Bad Name" 
      ]
    },
    "2468": {
      "album": "1999",
      "artist": "Prince",
      "tracks": [ 
        "1999", 
        "Little Red Corvette" 
      ]
    },
    "1245": {
      "artist": "Robert Palmer",
      "tracks": [ ]
    },
    "5439": {
      "album": "ABBA Gold"
    }
      };
      // Keep a copy of the collection for tests
      var collectionCopy = JSON.parse(JSON.stringify(collection));
      
SOLUTION!:      
      
      // Only change code below this line
      function updateRecords(id, prop, value) {
      // if property is not tracks and value is NOT empty
      if (prop != "tracks" && value !== ""){
      // update or set the value for the collection object's album [id] property [prop] 
      collection[id][prop] = value;
      
      // if property is "tracks" and value isnt empty  
      } else if (prop === "tracks" && value !== ""){
      // if property is "tracks" BUT album doesnt have tracks property (nested if statement)
        // check to see if that album from collection object DOES NOT has a property named "tracks"
      if (!collection[id].hasOwnProperty("tracks")){
        // if it does not then create an empty array
      collection[id][prop] = [];
        // then push the new value to album's corresponding property
      collection[id][prop].push(value);
      }  
      // (outer if statement) push value into end of album's existing tracks array
      collection[id][prop].push(value);
      // otherwise since value is empty, delete the given prop from album
      } else {
      delete collection[id][prop];
      }
      
      return collection;
      }
      
      // Alter values below to test your code
      updateRecords(5439, "artist", "ABBA");
