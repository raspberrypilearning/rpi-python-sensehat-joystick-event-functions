The Sense HAT joystick can be used to trigger function calls in response to being moved.

- For instance, you can tell your program to continually 'listen' for a specific event, such as the joystick being pushed up (`direction_up`), and to then trigger a function (called `pushed_up` in this example) in response.

	```python
	sense.stick.direction_up = pushed_up
	```

- The function triggered by the event can either have no parameters, or it can take the event as a parameter. In the example below, the event is simply printed out.

	```python
	def pushed_up(event):
		print(event)
	```

- This function would print a timestamp of the event, the direction in which the joystick was moved, and the specific action. The output would look similar to this:

	```python
	InputEvent(timestamp=1503565327.399252, direction=u'up', action=u'pressed')
	```

- Another useful example is the `direction_any` method:

	```python
	sense.stick.direction_any = do_thing
	```
- If you use this method as seen in the example, the `do_thing` function will be triggered in response to any joystick event. For instance, you could define the `do_thing` function so that it reports the exact event in plain English.

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
