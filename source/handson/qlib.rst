============================================================
``Qlib Walkthrough``
============================================================

Here is the list of HKEX symbols supported by Yahoo:`HKEX Symbols <../datasets/HKEX.csv>`_, concating list from http://eoddata.com/stocklist/HKEX.htm and
`HKETFs <../datasets/HKETF.csv>`_ parsed from https://www.hkex.com.hk/Market-Data/Securities-Prices/Exchange-Traded-Products?sc_lang=en .

.. code-block:: python

  import pandas as pd

  col_list = ["Symbol", "Description"]
  dtype = {'Symbol': str, 'Description': str}
  df = pd.read_csv("HKEX.csv", usecols=col_list, dtype = dtype, sep='\t')


  col_list = ["Date", 'Open', 'High', 'Low', 'Close', 'Adj Close', 'Volume']
  for symbol in df['Symbol']:
      url = f'https://query1.finance.yahoo.com/v7/finance/download/{symbol}.HK?period1=1087344000&period2=1623314082&interval=1d&events=history&includeAdjustedClose=true'
      try:
          df = pd.read_csv(url, usecols=col_list, sep=',')
      except:
          continue
      df = df.rename(columns={'Date': 'date', 'Open' : 'open', 'High': 'high', 'Low': 'low', 'Close': 'close', 'Adj Close': 'adj', 'Volume': 'vol'})
      df = df.dropna()
      df['factor'] = df['close'] / df['adj']
      df['open'] = df['close'] / df['factor']
      df['high'] = df['high'] / df['factor']
      df['low'] = df['low'] / df['factor']
      df['close'] = df['close'] / df['factor']
      df['change'] = df['close'].diff() # change is mandatory for PortAnaRecord, otherwise, can't get signals
  
      df.to_csv(f'output/{symbol}.csv', index=False)
      break


After downloading HKEX historical data, convert it to qlib format.

.. code-block:: bash

  python scripts/dump_bin.py dump_all --csv_path /home/lee/python/git/Datasets/HKEX/output/ \
  --qlib_dir ~/.qlib/qlib_data/hk_data --include_fields open,close,high,low,volume,factor,change \
  -symbol_field_name symbol --date_field_name date


To generate a collection of ETF:

.. code-block:: python

  import pandas as pd

  col_list = ["Symbol", "Date1", "Date2"]
  dtype = {'Symbol': str}
  df = pd.read_csv("~/.qlib/qlib_data/hk_data/instruments/all.txt", usecols=[0,1,2], names=col_list, dtype=dtype,sep='\t')
  df1 = pd.read_csv("HKETF.csv", usecols=[0], names=['Symbol'], dtype=dtype, sep='\t')
  
  dfetf = pd.merge(df, df1, on='Symbol', how='inner')
  dfetf.to_csv("~/.qlib/qlib_data/hk_data/instruments/etf.txt", index=False, header=False, sep='\t')
