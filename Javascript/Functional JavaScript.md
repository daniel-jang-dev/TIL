##1. FILTER: You want to remove unwanted elements based on a condition.

    var model = [];

    for(var i = 0 ; i < array.length ; i++) {
      if(array.indexOf(array[i] ===i))
      {
        model.push(array[i]);
      }
    }

    var model = array.filter(function(e, i, array) {
      return array.indexOf(e) === i;
    });
    
    //ES6
    var model = array.filter((x, i, array) => array.indexOf(x) === i);


##2. MAP: You want to translate/map all elements in an array to another set of values.

    var fahrenheit = [0, 32, 45, 50, 75, 80, 99, 120];

    var celcius = fahrenheit.map(function(elem) {
        return Math.round((elem - 32) * 5 / 9);
    });
    
    //ES6
    var celcius = fahrenheit.map(e => Math.round((e - 32) * 5 / 9));


##3. REDUCE: You want to find a cumulative or concatenated value based on elements across the array.

    var rockets = [
      { country:'Russia', launches:32 },
      { country:'US', launches:23 },
      { country:'China', launches:16 },
      { country:'Europe(ESA)', launches:7 },
      { country:'India', launches:4 },
      { country:'Japan', launches:3 }
    ];

    var sum = rockets.reduce(function(prev, elem) {
      return prev + elem.launches;
    });

    //ES6
    var sum = rockets.reduce((preVal, e) => preVal + e.launches);
