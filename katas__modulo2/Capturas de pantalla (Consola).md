# Ejercicio - Crear un paquete

## Crear un entorno virtual

Crea un entorno virtual mediante ``venv``

* Ejecutar en su terminal: ``python3 -m venv env`` o bien ``python -m venv env``

    ``
    python -m venv env
    ``
    
    ![1](https://user-images.githubusercontent.com/99307349/154655164-8be2656b-3294-4b6c-b377-f1e46a4be5d8.JPG)

    
    Ahora tienes un directorio (folder) ``env`` creado en tu terminal.

* Ejecuta el comando para activar el entorno virtual: ``source env/bin/activate``

    ```
    source env/bin/activate
    # Windows
    env\bin\activate
    
    o bien: 
    env\Scripts\activate

    # Linux, WSL or macOS
    source env/bin/activate
    ```
    
![2](https://user-images.githubusercontent.com/99307349/154655393-ad8eb529-0dc2-4cff-82ec-d44a960dc500.JPG)


## Instalar una biblioteca

Ahora que estás dentro de tu entorno virtual, puedes instalar una biblioteca y saber que la biblioteca solo existirá en el entorno virtual.

* Ejecuta el comando ``pip freeze`` para ver las bibliotecas instaladas en tu entorno:

    ```
    pip freeze
    ```

    No deberías obtener respuesta. A continuación, veamos cómo cambia la salida de ``pip freeze`` cuando se agrega una biblioteca (un paquete).

* Ejecuta el comando ``pip install`` para instalar una biblioteca:
   ```
   pip install python-dateutil
   ```
* Un gran mensaje de salida de texto dice que está instalando tu biblioteca, y debe terminar con la siguiente oración:

    ```
    Successfully installed python-dateutil-2.8.2 six-1.16.0
    ```
* Vuelve a ejecutar ```pip freeze``` para ver cómo ha cambiado tu lista de bibliotecas:
    ```
    pip freeze
    ```
* Ahora deberías ver la siguiente lista:
    ```
    python-dateutil==2.8.2
    six==1.16.0
    ```
    
![3](https://user-images.githubusercontent.com/99307349/154655634-6e6ab2e0-caa4-4520-973f-c6b60cb8a324.JPG)


### Desactivar un entorno virtual

Hasta ahora, has creado un entorno virtual y le has agregado un paquete. Sin embargo, es posible que estés trabajando en varios proyectos de Python y necesites cambiar entre ellos. Para hacer eso, debes salir (desactivar) tu entorno virtual.

Ejecuta el comando ``deactivate``:
```
deactivate
```

Observa cómo cambia el mensaje de tu terminal ``(env)`` a cómo se veía antes.

![4](https://user-images.githubusercontent.com/99307349/154655786-973313fc-27ff-49ae-929a-c03eb344f708.JPG)


## Fin del modulo 10.
