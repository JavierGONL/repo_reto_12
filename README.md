<div align='center'>
<figure> <img src="https://res.cloudinary.com/dm0p2ljin/image/upload/v1714416338/error-418_dtb3ak.png" alt="" width="300" height="auto"/></br>
<figcaption><b></b></figcaption></figure>
</div>


## Reto 12
1. Consulte que hacen los siguientes métodos de strings en python: endswith, startswith, isalpha, isalnum, isdigit, isspace, istitle, islower, isupper.
- "endswith(suffix, start=0, end=len(string))": Determina si una cadena de texto termina con una subcadena específica
```python
  cadena = "Hola, mundo!"
  print(cadena.endswith("mundo!"))  # True
  print(cadena.endswith("Hola"))  # False
```

- "startswith(prefix, start=0, end=len(string))": Determina si una cadena de texto comienza con una subcadena específica.
```python
cadena = "Hola, mundo!"
print(cadena.startswith("Hola"))  # True
print(cadena.startswith("mundo"))  # False
```
- "isalpha()": Determina si todos los caracteres de una cadena de texto son letras.
```python
cadena = "Hola, mundo!"
print(cadena.isalpha())  # False
cadena = "Hola"
print(cadena.isalpha())  # True
```
- "isalnum()": Determina si todos los caracteres de una cadena de texto son letras o dígitos.
```python
cadena = "Hola123"
print(cadena.isalnum())  # True
cadena = "Hola, mundo!"
print(cadena.isalnum())  # False
```
- "isspace()": Determina si todos los caracteres de una cadena de texto son espacios en blanco
```python
cadena = "   "
print(cadena.isspace())  # True
cadena = "Hola, mundo!"
print(cadena.isspace())  # False
```
- "istitle()": Determina si los primeros caracteres de cada palabra en una cadena de texto son mayúsculas.
```python
cadena = "Hola, Mundo!"
print(cadena.istitle())  # True
cadena = "hola, Mundo!"
print(cadena.istitle())  # False
```
- "islower()": Determina si todos los caracteres de una cadena de texto son minúsculas.
```python
cadena = "hola, mundo!"
print(cadena.islower())  # True
cadena = "Hola, mundo!"
print(cadena.islower())  # False
```
- "isupper()": Determina si todos los caracteres de una cadena de texto son mayúsculas.
```python
cadena = "HOLA, MUNDO!"
print(cadena.isupper())  # True
cadena = "Hola, mundo!"
print(cadena.isupper())  # False
```
2. Procesar el <a href="https://www.py4e.com/code3/mbox.txt">archivo</a> y extraer:
 - Cantidad de vocales
 - Cantidad de consonantes
 - Listado de las 50 palabras que más se repiten
```python
def contador_vocales_consonantes(texto: str) -> int:
    texto.lower()
    contador_vocales = 0
    contador_consonantes = 0
    consonantes = [98,99,100,102,103,104,106,107,108,109,110,112,113,114,115,116,118,119,120,121,122]
    vocales = [97,101,105,111,117]
    for letra in texto:
        if ord(letra) in vocales:
            contador_vocales += 1
        if ord(letra) in consonantes:
            contador_consonantes += 1    
    return contador_vocales,contador_consonantes

# volver a hacer
def top_50_palabras(texto):
    palabras = texto.split()
    contador_palabras = {}
    for palabra in palabras:
        if palabra in contador_palabras:
            contador_palabras[palabra] += 1
        else:
            contador_palabras[palabra] = 1
    contador_palabras = dict(sorted(contador_palabras.items(), key=lambda item: item[1], reverse=True))
    contador_palabras = dict(list(contador_palabras.items())[:50])
    return contador_palabras

if __name__ == "__main__":
    archivo = open('archivo_texto.txt', "r")
    texto = archivo.read()
    contador_vocal, contador_consonante = contador_vocales_consonantes(texto)
    print(f"El texto tiene: \n {contador_consonante} consonantes \n {contador_vocal} vocales")
    top_50_palabras_ = top_50_palabras(texto)
    print(f"Las 50 palabras mas repetidas son: {top_50_palabras_}")
    archivo.close()
```
