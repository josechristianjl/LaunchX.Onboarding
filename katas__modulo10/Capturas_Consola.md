# Módulo 10 - Manejo de errores

Incluso el código mejor escrito contendrá errores. Los errores pueden producirse debido a actualizaciones, archivos movidos u otros cambios inesperados. Afortunadamente, Python ofrece una amplia compatibilidad para el seguimiento y el control de errores.


## Tracebacks

1.
![1](https://user-images.githubusercontent.com/99307349/154656992-69fac2b5-03ae-4ca9-bdf5-3868cdb2e612.JPG)


Intenta crear un archivo de Python y asígnale el nombre *open.py*, con el contenido siguiente:

```
def main():
    open("/path/to/mars.jpg")

if __name__ == '__main__':
    main()
```
 2.
 ![2](https://user-images.githubusercontent.com/99307349/154657500-37cd93d6-78c1-419e-b996-25a8e9597ebb.JPG)

### Try y Except de los bloques

3.
![3](https://user-images.githubusercontent.com/99307349/154658006-b3c8be55-a1d2-4557-b906-8b6c22858d1d.JPG)


Aunque es común un archivo que no existe, no es el único error que podemos encontrar. Los permisos de archivo no válidos pueden impedir la lectura de un archivo, incluso si este existe. Vamos a crear un archivo de Python denominado config.py. El archivo tiene código que busca y lee el archivo de configuración del sistema de navegación:

```
def main():
    try:
        configuration = open('config.txt')
    except FileNotFoundError:
        print("Couldn't find the config.txt file!")


if __name__ == '__main__':
    main()
```

4.
![4](https://user-images.githubusercontent.com/99307349/154658326-1bfc1d5f-aec6-485b-b54e-be1b4c12002e.JPG)


Una manera poco útil de controlar este error sería detectar todas las excepciones posibles para evitar un traceback. Para comprender por qué detectar todas las excepciones es problemático, probaremos actualizando la función `main()`:
```
def main():
    try:
        configuration = open('config.txt')
    except Exception:
        print("Couldn't find the config.txt file!")
```

5.
![5](https://user-images.githubusercontent.com/99307349/154658450-3ec0e580-a93e-47b1-900f-7f31b3c34924.JPG)


Vamos a corregir este fragmento de código para abordar todas estas frustraciones. Revertiremos la detección de `FileNotFoundError` y luego agregamos otro bloque `except` para detectar `PermissionError`:

```
def main():
    try:
        configuration = open('config.txt')
    except FileNotFoundError:
        print("Couldn't find the config.txt file!")
    except IsADirectoryError:
        print("Found config.txt but it is a directory, couldn't read it")
```

6.
![6](https://user-images.githubusercontent.com/99307349/154658797-24f38aa6-2a84-46af-8924-c85af735b63a.JPG)


7.
![7](https://user-images.githubusercontent.com/99307349/154658828-ecf444dc-44ac-4a64-a99d-afd4f0af7fe7.JPG)


Cuando los errores son de una naturaleza similar y no es necesario controlarlos individualmente, puedes agrupar las excepciones como una usando paréntesis en la línea `except`. Por ejemplo, si el sistema de navegación está bajo cargas pesadas y el sistema de archivos está demasiado ocupado, tiene sentido detectar `BlockingIOError` y `TimeOutError` juntos:

```
def main():
    try:
        configuration = open('config.txt')
    except FileNotFoundError:
        print("Couldn't find the config.txt file!")
    except IsADirectoryError:
        print("Found config.txt but it is a directory, couldn't read it")
    except (BlockingIOError, TimeoutError):
        print("Filesystem under heavy load, can't complete reading configuration file")
```
**Sugerencia**

8.
![8](https://user-images.githubusercontent.com/99307349/154659286-f4d749d1-6795-4b0f-9d1f-9f77436e0967.JPG)


9.
![9](https://user-images.githubusercontent.com/99307349/154659299-fe6ad015-8bb4-44c8-99fc-59dcd5f414e3.JPG)


## Generación de excepciones
Los astronautas limitan su uso de agua a unos 11 litros al día. Vamos a crear una función que, con base al número de astronautas, pueda calcular la cantidad de agua quedará después de un día o más:

```
def water_left(astronauts, water_left, days_left):
    daily_usage = astronauts * 11
    total_usage = daily_usage * days_left
    total_water_left = water_left - total_usage
    return f"Total water left after {days_left} days is: {total_water_left} liters"
```

10.
![10](https://user-images.githubusercontent.com/99307349/154659631-ce815439-9e1c-4621-8ed2-c1d0414b3332.JPG)


11.
![11](https://user-images.githubusercontent.com/99307349/154659836-7b009875-19c5-4df8-973b-340abb85d04e.JPG)


12.
![12](https://user-images.githubusercontent.com/99307349/154660220-5adab52a-0190-40db-99a2-f006764c76c8.JPG)


13.
![13](https://user-images.githubusercontent.com/99307349/154660460-3112554d-c944-46eb-b959-74ad74998bd0.JPG)


## Resumen
Para ser un desarrollador eficaz, debes saber cómo funcionan las excepciones y cómo controlarlas. En este módulo, has descubierto cómo usar la salida de excepción para la depuración, cómo detectar y generar excepciones y, por último, cómo afecta a la lógica de un programa cuando se producen excepciones.


## Fin del modulo 10.
