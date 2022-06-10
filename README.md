# <a id="top">ProjecteFinal-Grup4: Furbo</a>

Membres del Grup: Adrián Gil, Gerard Pedrero, Carlos Abel Silva.

## Idea principal: 
L’idea del nostre projecte és crear un videojoc web. Consta d’un mode de joc on tu ets l’entrenador de la selecció que tu vols, pots escollir l’11 inicial i simular 	tota la competició. Hi hauran els 23 jugadors reals a totes les seleccions. Cada usuari podrà iniciar només una partida.

## Taula de tasques: 

| Tasques | Qui les fà | Data espereada | Data real |
| ------ | ------ | ------ | ------ |
| Crear base de dades | Carlos | 19 Abril-19 Abril | 19 Abril-19 Abril |



## Llista de tasques: 

[x] Crear base de dades



## Punts importants: 

El nostre projecte està, majoritàriament, fet amb PHP. També s'utilitza JQuery, base de dades SQL i estil css.

### Creació d'usuari: 

Per la creació d'usuaris, ho fem amb php de la següent manera:



Aquestes sentències, crean l'usuari a la taula d'users de la nostre base de dades però, l'usuari no està actiu encara, fins que no confirmi el mail amb el codi de verificació. El codi el creem de la següent forma.



Creem una cadena amb tots els caràcters i una array buida, i amb un bucle i un random, anem omplint l'array amb 8 caràcters aleatoris i amb l'implode posem tota l'array en una variable, sense posicions. Per acabar, enviem el mail amb la funció mail de php.



### Menú Jquery: 

El nostre menú, consta de 4 apartats: Equip, jugar partit, partits del dia i ranking d'usuaris. Tots els apartats són divs que, només entrar-hi, s'amagan.



Les imatges són botons, quan fas clic a un botó fan que s'amagui el div general i surti el div del botó que has clicat.





### Mòbil: 

Si accedeixes a la web desde un dispositiu mòbil, surt un footer que et dona l'opció de baixar-te la aplicació de la nostre web. El footer es un div que, amb css, apareix quan la pantalla del usuari es menor a 768px.

```html

<div id="div-cookies" style="display: none;">
    Necesitamos usar cookies para que funcione todo, si permanece aquí acepta su uso, más información en
    <a hreflang="es" href="/info/aviso-legal">Aviso Legal</a>y la
    <a hreflang="es" href="/info/politica-de-privacidad">Política de Privacidad</a>.
    <button type="button" class="btn btn-sm btn-primary" onclick="acceptCookies()">
    Acepto el uso de cookies
    </button>
    </div>
    <style>
      #cookies{
        position: absolute;
        bottom: 5%;
        left: 0;
        text-align: center;
        font-size: 20px;
        background-color: gray;
      }
      </style>
    <div id="cookies">
    Este porfolio utiliza la politica de cookies, para mas información acerca de las cookies en lordsergio.online pulsa el siguiente vinculo
     <a href="https://www.youtube.com/watch?v=CXm7hPs_als" target="_blank">Politca de cookies</a>
    <button onclick="guardarDatos()">Aceptar</button>
    </div>
    <script>
      let data = new Date;
        let storage = window.localStorage;
        let diaAnterior = JSON.parse(localStorage.getItem('dia'));
    
        if( data.getDate() - diaAnterior >3 || diaAnterior == null){
            //Aparece el menu si han pasado menos de 3 dias o si no hay valores en el localStorage
            document.getElementById("cookies").style.display = "block";
        }else {
          document.getElementById("cookies").style.display = "none";
        }
    
    function guardarDatos(){
        //Cuando se pulsa el botón de aceptar cookies se cierra la ventana
        document.getElementById("cookies").style.display = "none";
        localStorage.setItem('dia',data.getDate());
    }
    </script>

```



