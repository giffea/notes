# main ()
```python
def main():
	try:
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
            '--output',
            default='out.csv',
            dest='outputFile',
            help='output file name (default: out.csv)',
        )
        args = parser.parse_args()
        
    except ValueError as error:
        logger.exception(error.args)  
        
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
# Logger
```python
import logging
import sys


class Logger(object):
    EXIT_SUCCESS = 0
    EXIT_ERROR = 1
    EXIT_WARNING = 2

    def __init__(self, name, level=logging.INFO):
        self.has_error = False

        self.logger = logging.getLogger(name)
        self.logger.setLevel(level)
        self.logger.propagate = False  # avoid duplicate message on HWRD
        self.formatter = logging.Formatter('%(levelname)s: %(message)s')

        self.file_handler = logging.FileHandler('log', mode='w')
        self.file_handler.setFormatter(self.formatter)
        self.file_handler.setLevel(level)
        self.logger.addHandler(self.file_handler)

        self.console_handler = logging.StreamHandler(sys.stdout)
        self.console_handler.setFormatter(self.formatter)
        self.logger.addHandler(self.console_handler)

    def critical(self, message):
        self.logger.critical(message)

    def error(self, message1, message2=None):
        if message2 is None:
            message = message1
        else:
            message = 'Expected: {}\n       Actual  : {}'.format(
                message1,
                message2,
            )

        self.logger.error(message)
        self.has_error = True

    def exception(self, message):
        self.logger.exception(message)

    def info(self, message1, message2=None):
        if message2 is None:
            message = message1
        else:
            message = 'Expected: {}\n        Actual  : {}'.format(
                message1,
                message2,
            )
        self.logger.info(message)

    def warning(self, message1, message2=None):
        if message2 is None:
            message = message1
        else:
            message = 'Expected: {}\n         Actual  : {}'.format(
                message1,
                message2,
            )
        self.logger.warning(message)

    def create_log_file(self, report_dir):
        self.logger.removeHandler(self.file_handler)
        self.file_handler = logging.FileHandler(
            report_dir + '/log.csv', mode='w')
        self.file_handler.setFormatter(self.formatter)
        self.file_handler.setLevel(logging.INFO)
        self.logger.addHandler(self.file_handler)
  ```
# Excel
```python
import pandas as pd
from xlsxwriter.utility import xl_range, xl_rowcol_to_cell

writer = pd.ExcelWriter(self.file_name, engine='xlsxwriter')
df.to_excel(
    writer,
    header=False,
    index=False,
    na_rep='=#REF!',
    sheet_name=sheet_attr.name,
    startrow=sheet_attr.first_data_row,
    startcol=sheet_attr.first_data_col
)
worksheet = writer.sheets[sheet_attr.name]

writer.save()
```

# 

Python virtualenv

‌

## 

Setup virtualenv

‌

[[Python] How to set up python virtual environment](http://hiwiki.mediatek.inc/display/ITSW/%5BPython%5D+How+to+set+up+python+virtual+environment)

‌

1.  set ~/.pip/pip.conf
    
    [global] index-url = http://your_ip/pypi/simple [install] trusted-host = your_ip
    
2.  cd ~/local virtualenv -p python3.6 pyEnv source pyEnv/bin/activate
    
3.  Install required modules by one of following method (a or b).
    
    1.  pip install -r requirements.txt
        
    2.  pip install -U pip setuptools pip install 'Cython>=0.20,<0.25' pip install cassandra-driver jupyter matplotlib pandas numpy scipy
        
    

‌

## 

Usage

‌

-   cd ~/TPPA/local
    
-   source pyEnv/bin/active # enable virtualenv
    
-   deactiveate # disable virtaulenv

## Export virtualenv setting for others
-   pip freeze > requirements.txt
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM0ODc2NjU2MywtMTQ3ODc4NDM2NCwxMj
U2MTYwMDc4LDE1ODQxOTgzMDQsMjAwNTgzMTEwNCwtNzAxMTcw
MjA0XX0=
-->