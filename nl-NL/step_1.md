De Sense HAT-joystick kan worden gebruikt om functieaanroepen te activeren in reactie op verplaatsing.

- Je kunt bijvoorbeeld je programma vertellen om voortdurend te 'luisteren' naar een specifieke gebeurtenis, zoals de joystick die omhoog wordt geduwd (`direction_up`), en vervolgens een functie (in dit voorbeeld `omhoog_geduwd` genoemd) te activeren.

    ```python
    sense.stick.direction_up = omhoog_geduwd
    ```

- De functie die door de gebeurtenis wordt geactiveerd, kan geen parameters hebben of de gebeurtenis als parameter nemen. In het onderstaande voorbeeld wordt de gebeurtenis eenvoudig afgedrukt.

    ```python
    def omhoog_geduwd(gebeurtenis):
        print(gebeurtenis)
    ```

- Met deze functie wordt een tijdstempel van de gebeurtenis, de richting waarin de joystick werd verplaatst en de specifieke actie afgedrukt. De output ziet er ongeveer zo uit:

    ```python
    InputEvent(timestamp=1503565327.399252, direction=u'up', action=u'pressed')
    ```

- Een ander nuttig voorbeeld is de methode `direction_any`:

    ```python
    sense.stick.direction_any = doe_ding
    ```
- Als je deze methode gebruikt, zoals te zien in het voorbeeld, wordt de functie `doe_ding` geactiveerd als reactie op een joystickgebeurtenis. Je kunt bijvoorbeeld de functie `doe_ding` definiëren, zodat deze de exacte gebeurtenis in gewoon Engels rapporteert.

    ```python
    def doe_ding(gebeurtenis):
        if gebeurtenis.action == 'press':
            print('Je hebt me ingedrukt')
            if gebeurtenis.direction == 'up':
                print('Omhoog')
            elif gebeurtenis.direction = = 'down':
                print('Omlaag')
        elif gebeurtenis.action == 'released':
            print('Je hebt me losgelaten')
    ```
