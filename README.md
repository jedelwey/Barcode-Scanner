#Barcode Scanner
Barcode Scanner es una aplicación de demostración/tutorial para aprender a usar el Barcode Scanner (Escaner de código de barras/QR) con Phonegap. Para ello simplemente hay que tener en cuenta
  - Archivo config.xml
  - index.js

El resto de los archivos son simplemente para poner la aplicación mucho más bonita usando [Pure CSS].
En el archivo config.xml lo más importante es la linea:
    
    <gap:plugin name="com.phonegap.plugins.barcodescanner" version="2.0.0" />
Esta línea lo que hace es indicar a [Phonegap Build] que tiene que usar y añadir el [Plugin Barcode Scanner] y añadirlo a la compilación.

Y en el archivo index.js explico como se usa este método:

    function scanear(){
        cordova.plugins.barcodeScanner.scan(
            function (result) {  
                var codigoQR=result.text;
                $('#resultado').html(codigoQR);
            }, 
            function (error) {
                notificacion("Ha ocurrido un error al escanear.");
            }
        );
    };
*   Si el scaneo del barcode Scanner funciona se ejecuta la función result y si no, pues se ejecuta la función error dependiendo del callback que nos traiga el plugin.
*   Guardamos el resultado del código QR o código de barras en una variable, en mi caso codigoQR. Para ello parseamos el resultado a texto.
*   Introducimos esa variable en el html en un campo que tenemos creado, en mi caso un <span> con un id resultado donde saldrá el resultado del escaneo.


[Pure CSS]:http://purecss.io/
[Phonegap Build]:https://build.phonegap.com
[Plugin Barcode Scanner]:https://build.phonegap.com/plugins/951
