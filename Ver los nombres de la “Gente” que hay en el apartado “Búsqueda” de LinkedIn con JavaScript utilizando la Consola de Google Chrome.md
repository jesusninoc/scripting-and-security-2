# Ver los nombres de la “Gente” que hay en el apartado “Búsqueda” de LinkedIn con JavaScript utilizando la Consola de Google Chrome
## JavaScript, Web 
### URL: https://www.jesusninoc.com/2017/08/09/ver-los-nombres-de-la-gente-que-hay-en-el-apartado-busqueda-de-linkedin-con-javascript-utilizando-la-consola-de-google-chrome/
```JavaScript
var divs = $('.actor-name');
for(var i = 0; i < divs.length; i++){
console.log(divs[i].innerHTML);
}

```
