# 装饰器

```python
import functools

# 装饰器参数可带可不带，log()或log('execute')均支持
def log(*args):
	text = 'call'
	for n in args:
		text = n
	def decorator(func):
		@functools.wraps(func)
		def wrapper(*args, **kw):
			print('%s %s():' % (text, func.__name__))
			return func(*args, **kw)
		return wrapper
	return decorator
```