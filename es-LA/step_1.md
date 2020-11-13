El joystick Sense HAT puede ser usado para activar llamadas de función en respuesta a ser movido.

- Por ejemplo, puedes decirle a tu programa que ‘escuche’ continuamente un evento específico, como el joystick que está siendo empujado hacia arriba (`direction_up`) y luego desencadenar una función (llamada `pushed_up`, en este ejemplo) como respuesta.

    ```python
    sense.stick.direction_up = pushed_up
    ```

- La función activada por el evento puede no tener parámetros o puede tomar el evento como un parámetro. En el ejemplo siguiente, el evento es simplemente impreso.

    ```python
    def pushed_up(event):
        print(event)
    ```

- Esta función imprimiría una marca de tiempo del evento, la dirección en la que el joystick se movió y la acción específica. La salida se vería similar a esto:

    ```python
    InputEvent(timestamp=1503565327.399252, direction=u'up', action=u'pressed')
    ```

- Otro ejemplo útil es el método `direction_any`:

    ```python
    sense.stick.direction_any = do_thing
    ```
- Si utilizas este método como se ve en el ejemplo, la función `do_thing` se activará en respuesta a cualquier evento del joystick. Por ejemplo, puedes definir la función `do_thing` para que reporte el evento exacto en inglés simple.

    ```python
    def do_thing(event):
        if event.action == 'pressed':
            print('You pressed me')
            if event.direction == 'up':
                print('Up')
            elif event.direction == 'down':
                print('Down')
        elif event.action == 'released':
            print('You released me')
    ```
