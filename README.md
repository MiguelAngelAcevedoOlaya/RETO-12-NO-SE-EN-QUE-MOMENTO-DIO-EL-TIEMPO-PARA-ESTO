# RETO 12
## PUNTO 1
### Consulte que hacen los siguientes métodos de strings en python: endswith, startswith, isalpha, isalnum, isdigit, isspace, istitle, islower, isupper.

* endswith = Permite analizar el sufijo de una cadena, en el que si el que ponemos en el codigo es igual al de la cadena imprimra true, y en caso que no, false. Ademas podemos modificar donde inicia y donde finaliza su busqueda en la cadena: ``` endswith(suffix[, start[, end]]) ```
* startswith = Completamente lo contrario de endswith, este permite analizar si el prefijo es el que ponemos en el codigo, osea el inicio de la cadena y al igual que el otro podemos modificar donde inicia y donde acaba la busqueda: ```startswith(prefix[, start[, end]])```
* isalpha = Analiza una cadena, en la que si solo contiene letras y no es vacia imprimira true, de lo contrario false. ```isalpha()```
* isalnum = Paracido a isalpha, pero este analzia si la cadena es unicamente caracteres alfanúmericos y no debe estar vacia. ```isalnum()```
* isdigit = Determina si la cadena contiene unicamente números y no tience vacios. ```isdigit()```
* issspace = Determina si la cadena esta llena completamente de espacios vacios. ```isspace()```
* isstitle = Determina si la cadena esta en formato de titulo, osea que la primera letra de cada palabra este en mayuscula. ```istitle()```
* islower = Determina si en la cadena todas sus letras se encuentran en minuscula. ```islower()```
* isupper = Determina si en la cadena todas sus letras se encunetran en mayuscula. ```isupper()```
## PUNTO 2
### Procesar el archivo y extraer:

* Cantidad de vocales
* Cantidad de consonantes
* Listado de las 50 palabras que más se repiten

#### 2.1 Y 2.2

Para los dos puntos se uso el with open, que permite trabajar archivos de texto, pero los cierra apenas termina la ejecución del codigo. Utilizamos una variable que permite leer todo el archivo.

Establecemos unos contadores, uno para vocales y otro para consonantes. Para que en un ciclo for si encunetra una vocal, o consnate sume uno a sus respectivos contadores. Para luego imprimir el númerod e vocales y consonates que aparen en todo el archivo.txt
```
with open("mbox-short.txt", "r") as archivo: # Abrimos el archivo con with 
    contenido = archivo.read() # Variable que lee el archivo
    num_vocales = 0 # contador para vocales
    num_consonantes = 0 # Contador para consonantes
    for letra in contenido: # Ciclo for que recorre la lista
      if letra.lower() in "aeiouáéíóú": 
        num_vocales += 1 # busca si hay vocal en minuscula o mayuscula, con tilde o sin ella y suma uno al contador
      elif letra.lower() in "bcdfghjklmnñpqrstvwxyz":
        num_consonantes += 1 # busca si hay consontate en minuscula o mayuscula y suma uno al contador
    print("El número de vocales es: " +str(num_vocales)) #vocales
    print("El número de consonantes es: " +str(num_consonantes)) # consonantes 
```

#### 2.3

Utilizamos el mismo codigo para trabajar el archivo txt, utlizamos el .split() para separar los elementos por cada espacio que halla entre ellas, permitiendo obtener las palabras que estan en todo el archivo. Utilizamos el counter, que se usa importando collections, este permite sacar cuantas veces aparece la palabra, y ademas utilizando el most_common podemos extraer las 50 que más aparecen. Al final solo estabelcimos un codigo para imprimirlo más bonito.

```
from collections import Counter # Importamos libreria para contar
with open("mbox-short.txt", "r") as archivo: # Abrimos el archivo con with 
    contenido = archivo.read() # Variable que lee el archivo
    contenido = contenido.split() # separa cada elemento por palabras, considerando los espacios entre ellas
    palabras = Counter(contenido).most_common(50) # agtega a la variable palabra, la lista de las 50 que mas aparecen
    m=0 #contador
    print("Las 50 palabras que más se repiten son: ")
    for i in palabras: #ciclo for para imprimir en lista
      m += 1 # contador para enumerar palabras
      print("Palabra número " +str(m)+ ": " +str(i) ) #50 palabra que más se repiten
```
