# unittest

```python
import unittest

class MyTestCase(unittest.TestCase):
    @classmethod
    def setUpClass(cls):
        pass

    @classmethod
    def tearDownClass(cls):
        pass

    def test_something(self):
        self.assertEqual(True, False)


if __name__ == '__main__':
    unittest.main(verbosity=2)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwMTE3MDIwNF19
-->