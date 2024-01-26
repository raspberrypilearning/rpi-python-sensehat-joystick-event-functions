Le joystick Sense HAT peut être utilisé pour déclencher des appels de fonction en réponse à un déplacement.

- Par exemple, tu peux dire à ton programme d'« écouter » continuellement un événement spécifique, comme le fait de pousser le joystick vers le haut (`direction_up`), et de déclencher ensuite une fonction (appelée `pushed_up` dans cet exemple) en réponse.

    ```python
    sense.stick.direction_up = pushed_up
    ```

- La fonction déclenchée par l'événement peut soit n'avoir aucun paramètre, soit prendre l'événement comme paramètre. Dans l'exemple ci-dessous, l'événement est simplement imprimé.

    ```python
    def pushed_up(event):
        print(event)
    ```

- Cette fonction imprime un horodatage de l'événement, la direction dans laquelle le joystick a été déplacé et l'action spécifique. Le résultat ressemblerait à ceci :

    ```python
    InputEvent(timestamp=1503565327.399252, direction=u'up', action=u'pressed')
    ```

- Un autre exemple utile est la méthode `direction_any` :

    ```python
    sense.stick.direction_any = do_thing
    ```
- Si tu utilises cette méthode comme le montre l'exemple, la fonction `do_thing` sera déclenchée en réponse à tout événement lié au joystick. Par exemple, tu pourrais définir la fonction `do_thing` de façon à ce qu'elle signale l'événement exact en anglais simple.

    ```python
    def do_thing(event):
        if event.action == 'pressed':
            print('Tu m'as pressé')
            if event.direction == 'up':
                print('Haut')
            elif event.direction == 'down':
                print('Bas')
        elif event.action == 'released':
            print('Tu m'as relaché')
    ```
