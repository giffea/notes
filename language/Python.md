# main ()
```python
        parser = argparse.ArgumentParser(
            description="haha."
        )
        parser.add_argument(
            'db_file',
            help='the project which you want to query',
            nargs=1,
        )
        parser.add_argument(
            '-o',
            default='out.csv',
            dest='outputFile',
            help='output file name (default: out.csv)',
        )
        args = parser.parse_args()
        
if __name__ == '__main__':
    main()
```

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
eyJoaXN0b3J5IjpbNzIwNTY3Mjk3LDIwMDU4MzExMDQsLTcwMT
E3MDIwNF19
-->