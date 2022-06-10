# <a id="top">ProjecteFinal-Grup4: Furbo</a>

Membres del Grup: Adrián Gil, Gerard Pedrero, Carlos Abel Silva.

## Idea principal: 
L’idea del nostre projecte és crear un videojoc web. Consta d’un mode de joc on tu ets l’entrenador de la selecció que tu vols, pots escollir l’11 inicial i simular 	tota la competició. Hi hauran els 23 jugadors reals a totes les seleccions. Cada usuari podrà iniciar només una partida.

## Taula de tasques: 

| Tasques | Qui les fà | Data espereada | Data real |
| ------ | ------ | ------ | ------ |
| Crear base de dades | Carlos | 19 Abril-19 Abril | 19 Abril-19 Abril |
| Omplir base de dades amb jugadors reals | Gerard, Adrián, Carlos | 19 Abril-21 Abril | 19 Abril-20 Abril |
| Login | Carlos | 21 Abril-21 Abril | 21 Abril-21 Abril |
| Selecció d'11 inicial | Carlos | 26 Abril-5 Maig | 3 Maig-10 Maig |
| Enfrontament d'equips (Torneig/Calendari) | Carlos, Gerard | 12 Maig-17 Maig | 12 Maig-19 Maig |
| Afegir 3 seleccions més i música pel menú del joc | Adrián | 10 Maig-12 Maig | 10 Maig-24 Maig |

## Llista de tasques: 

[x] Crear base de dades

[x] Omplir base de dades amb jugadors reals

[x] Login

[x] Selecció d'11 inicial

[x] Enfrontament d'equips (Torneig/Calendari)

[x] Afegir 3 seleccions i música

## Punts importants: 

El nostre projecte està, majoritàriament, fet amb PHP. També s'utilitza JQuery, base de dades SQL i estil css.

### Creació d'usuari: 

Per la creació d'usuaris, ho fem amb php de la següent manera:

```php

$sql="INSERT INTO users (id_user, name_user, mail_user, pass_user, actiu_user, partida_user, seleccio_triada, w_totals, d_totals, winrate) VALUES (NULL, '$user', '$mail', '$passw', 0, 0, 0,0, 0,0)";
$result = $mysqli->query($sql);

```

Aquestes sentències, crean l'usuari a la taula d'users de la nostre base de dades però, l'usuari no està actiu encara, fins que no confirmi el mail amb el codi de verificació. El codi el creem de la següent forma.

```php

$comb = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890';
$pass = array(); 
$combLen = strlen($comb) - 1; 
for ($i = 0; $i < 8; $i++) {
     $n = rand(0, $combLen);
     $pass[] = $comb[$n];
} 
$codigo=implode($pass);

```

Creem una cadena amb tots els caràcters i una array buida, i amb un bucle i un random, anem omplint l'array amb 8 caràcters aleatoris i amb l'implode posem tota l'array en una variable, sense posicions. Per acabar, enviem el mail amb la funció mail de php.

```php

$mensaje = "Codigo de verificación: ".$codigo;
mail($mail, 'Hola '.$user.', verifica tu correo:', $mensaje);

```

[Veure arxiu](./index.php)

### Seleccions aleatories: 

Un cop has escollit la teva selecció, s'escullen aleatoriament 7 seleccions més de les 11 que hi han disponibles(Són 12 contant la que ja has ecollit). Ho fem fent un select a la base de dades de totes les seleccions(Que no són la que ja has escollit tú), posant-les totes a una array i, amb un random, s'escullen 7 seleccions de les 11 disponibles. Per acabar, fem un shuffle per fer el enfrontament d'equips encara més aleatori.

```php

$sql="SELECT id_seleccion FROM selecciones WHERE id_seleccion!='$seleccio'";
$result = $mysqli->query($sql);

while($row=$result->fetch_array()){
   $ids[$a]=$row["id_seleccion"];
   $a++;
}

$claves_aleatorias = array_rand($ids, 7);
shuffle($claves_aleatorias);

```

[Veure arxiu](./inicial.php)

### Menú Jquery: 

El nostre menú, consta de 4 apartats: Equip, jugar partit, partits del dia i ranking d'usuaris. Tots els apartats són divs que, només entrar-hi, s'amagan.

![image](https://user-images.githubusercontent.com/72878201/170289135-1d5bdb5c-3f0c-469b-81e7-969524a3bb8d.png)

Les imatges són botons, quan fas clic a un botó fan que s'amagui el div general i surti el div del botó que has clicat.

```js

$("#equipo,#defensas,#centrocampista,#delantero,#calendario,#taulasclasi").hide();

$(".btequipo").click(function(){
     $("#equipo").show();
     $("#menu,#calendario,#taulasclasi").hide();
});
$(".btmenu").click(function(){
     $("#equipo,#calendario,#taulasclasi").hide();
     $("#menu").show();
});
$(".calendario").click(function(){
     $("#equipo,#taulasclasi,#menu").hide();
     $("#calendario").show();
});
$(".tClas").click(function(){
     $("#equipo,#menu,#calendario").hide();
     $("#taulasclasi").show();
});

```

[Veure arxiu](./menu.php)

### Mòbil: 

Si accedeixes a la web desde un dispositiu mòbil, surt un footer que et dona l'opció de baixar-te la aplicació de la nostre web. El footer es un div que, amb css, apareix quan la pantalla del usuari es menor a 768px.

```html

<div class="footerapk">
    <p>Descarga la app para móvil! <a href="apk/furbo.zip" target="_blank">Descarga Aquí</a></p>
</div>

```

```css

.footerapk {
    display: none;
}

@media screen and (max-width: 768px) {
    .footerapk {
       display: block;
       position: fixed;
       left: 0;
       bottom: 0;
       width: 100%;
       background-color: rgba(0,0,0,0.50);
       color: white;
       text-align: center;
    } 
}

```

![image](https://user-images.githubusercontent.com/72878201/170296427-3fb4483e-8020-4fc2-bd9d-a267d2abf0bf.png)

Quan li dones a descargar, se't descarrega un zip amb una apk que pots instal·lar al teu dispositiu móbil. 

[Veure arxiu](./css/css.css)

[Pujar](#top)
