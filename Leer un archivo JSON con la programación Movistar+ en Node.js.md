# Leer un archivo JSON con la programación Movistar+ en Node.js
## JavaScript, Node.js 
### URL: https://www.jesusninoc.com/2018/06/22/leer-un-archivo-json-con-la-programacion-movistar-en-node-js/
```JavaScript
var http = require('https');

var url = 'https://www.jesusninoc.com/s/movistar.php';
 
 http.get(url, function(res) {
      var body = '';
 
      res.on('data', function(chunk) {
         body += chunk;
      });
 
      res.on('end', function() {
        var jsonData = JSON.parse(body)
        for (var i = 0; i < jsonData.length; ++i) {
          console.log(jsonData[i].Nombre);
          console.log(jsonData[i].Pases[0].Titulo);
          console.log("----------------------------------");
        }
      });
    }).on('error', function(e) {
      console.log("Error: " + e.message);
 });

```
