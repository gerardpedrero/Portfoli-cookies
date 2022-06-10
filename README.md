# <a id="top">Activitat recuperacions Portfolio-Cookies</a>



## Idea principal: 
L’idea del nostre projecte és crear un videojoc web. Consta d’un mode de joc on tu ets l’entrenador de la selecció que tu vols, pots escollir l’11 inicial i simular 	tota la competició. Hi hauran els 23 jugadors reals a totes les seleccions. Cada usuari podrà iniciar només una partida.

## Taula de tasques: 

| Tasques | Qui les fà |
| ------ | ------ |
| Fer la feina | Gerard |



## Llista de tasques: 

[x] Fer que las cookies apareixin 
[x] Fer que las cookies torini a apareixa cada 3 dies
[x] Fer el readme





### Realitzacio de la feina: 

En la fenia he utilitzat el localstorage per poder guardar el dia que aconegueixo amb la comnada data.getDate() i despres comparo el dia guardat amb el actual 
i si el dia de guardat te una diferencia de 3 dies o mes al actual et tornara a sortir per acceptar les cookies que nomes es un div que enesñem y amagem

```html

<div id="div-cookies" style="display: none;">
    Necesitamos utilizar cookies para que funcione todo, si permanece aquí acepta su uso, más información en
    <a hreflang="es" href="/info/aviso-legal">Aviso Legal</a>y la
    <a hreflang="es" href="/info/politica-de-privacidad">Política de Privacidad</a>.
    <button type="button" class="btn btn-sm btn-primary" onclick="acceptCookies()">
    Acepto el uso de cookies
    </button>
    </div>
    <style>
      #cookies{
        position: absolute;
        text-align: center;
        font-size: 20px;
        background-color: gray;
      }
      </style>
    <div id="cookies">
    Este porfolio utiliza la politica de cookies, para mas información pulsa el siguiente vinculo
     <a href="https://www.youtube.com/watch?v=CXm7hPs_als" target="_blank">Politca de cookies</a>
    <button onclick="guardarDatos()">Aceptar</button>
    </div>
    <script>
      let data = new Date;
        let storage = window.localStorage;
        let diaAnterior = JSON.parse(localStorage.getItem('dia'));
    
        if( data.getDate() - diaAnterior >3 || diaAnterior == null){
            
            document.getElementById("cookies").style.display = "block";
        }else {
          document.getElementById("cookies").style.display = "none";
        }
    
    function guardarDatos(){
      
        document.getElementById("cookies").style.display = "none";
        localStorage.setItem('dia',data.getDate());
    }
    </script>

```



