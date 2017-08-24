- The Sense HAT joystick can be used to trigger function calls, whenever it is used.

- For instance, you could set your program to continually "listen" out for a specific event, such as the joystick being pushed up.

	```python
	sense.stick.direction_up = pushed_up
	```

- This would then trigger a function called `pushed_up`. The function can either have no parameters, or a single parameter, which would be the event. In the example below, the event is simply printed out.

	```python
	def pushed_up(event):
		print(event)
	```

- The result of this function would be something like the following

	```python
	InputEvent(timestamp=1503565327.399252, direction=u'up', action=u'pressed')
	````

- This is a timestamp of the event, the direction the joystick was moved, and the specific action.

- Perhaps a more useful example is the `direction_any` method.

	```python
	sense.stick.direction_any = do_thing
	```
- Now the `do_thing` function will be called on any joystick event. So you could now write a function that reports the exact event in plain English.

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
