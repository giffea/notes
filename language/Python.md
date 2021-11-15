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

# setdefault
dict_a.setdefault(key, []).append(value0)

# unittest
python3 -m unittest discover . -v

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

sheets = pd.read_excel('xxx.xlsx', sheet_name=None, engine='openpyxl')
```

# Pandas
``` python3
df = indexl_df['info'].str.extract('.*stall=(?P<info>\S+)')
df2 = df['info'].str.split('|', expand=True)
sys_stall_df = pd.concat([indexl_df[['time']], df2], axis=1)
```

# Python virtualenv

## Setup virtualenv

1.  set ~/.pip/pip.conf
    [global] index-url = http://your_ip/pypi/simple [install] trusted-host = your_ip
2.  cd ~/local virtualenv -p python3.6 pyEnv source pyEnv/bin/activate
3.  Install required modules by one of following method (a or b).
    1.  pip install -r requirements.txt 
    2.  pip install -U pip setuptools pip install 'Cython>=0.20,<0.25' pip install cassandra-driver jupyter matplotlib pandas numpy scipy

## Usage
-   source pyEnv/bin/active # enable virtualenv
-   deactiveate # disable virtaulenv

## Export virtualenv setting for others
-   pip freeze >requirements.txt

# Seaborn
```python
import matplotlib.pyplot as plt
import seaborn as sns
plt.figure(figsize=(18, 8))
plt.xticks(rotation=45)
df = pd.DataFrame(data, columns=['interval', 'count', 'type'])
ax = sns.barplot(x='interval', y='count', hue='type', data=df)
ax.set(title='', xlabel='', ylabel='')
fig = ax.get_figure()
fig.savefig(f'xx.png', bbox_inches="tight", facecolor="#FFFFFF")
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4ODMxMTUyNzYsLTEzMjA5NjA0NTcsLT
UyMDg1ODA1MSwtMTM0NjQ0NjI2LDE4OTc0MzI1MDksLTk3NDg4
NzcsLTE0Nzg3ODQzNjQsMTI1NjE2MDA3OCwxNTg0MTk4MzA0LD
IwMDU4MzExMDQsLTcwMTE3MDIwNF19
-->