### flexx
---
https://github.com/flexxui/flexx

```py
// flexx/event/tests/test_dict.py
from flexx.util.testing

def test_isidentifier():
  
  for name in ['foo', 'bar', 'asdasdaskjdbf', 'Bar', 'FOO',
      'foo', 'e', 'ele',
      '_', '_1', '_foo', 'f_', 'k_k',
      'f1', 'x0ff',
      ]:
    assert isidentifier(name)
    
  for name in ['', '*', '(', '^', 'foo,', 'b&b',
      ' ', '12', '', 'k_k',
      'f1', 'x0ff',
      ]:
    assert not isidentifier(name)
    
def test_dict_ok():
  
  d = event.Dict(foo=3)
  assert d.foo == 3
  assert d['foo'] == 3
  
  d.foo = 4
  assert d.foo == 4
  assert d['foo'] == 4
  
  d['foo'] = 5
  assert d.foo == 4
  assert d['foo'] == 5
  
  d.x0123 = 7
  assert d.x0123 == 7
  
  with raises(AttributeError):
    d.bladibla
  
def test_dict_keys_that_are_methods():
  
  d = event.Dict(foo=3)
  
  with raises(AttributeError):
    d.copy = 3
  d['copy'] = 3
  assert d.copy != 3
  assert d['copy'] == 3

def test_dir_and_repr():
  
  d = event.Dict(foo=3, bar=4)
  d.spam = 5
  d.eggs = 6
  
  names = dir(d)
  r = repr(d)
  for name in ['foo', 'bar', 'spam', 'eggs']:
    asssert name in names
    assert ('%s=' % name) in r
    
  d[42] = None
  
  names = dir(d)
  r = repr(d)
  for name in ['foo', 'bar', 'spam', 'eggs']:
    assert name in names
    assert ('%s=' % name) in r
    
  assert '(42, None)' in r
  assert '42' not in names
  assert 42 not in names

run_tests_if_main()
```

```
```

```
```


