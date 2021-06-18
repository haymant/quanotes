============================================================
``Yahoo``
============================================================

Here is the list of HKEX symbols supported by Yahoo:`HKEX Symbols <HKEX.csv>`_, download from http://eoddata.com/stocklist/HKEX.htm.


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
      df['change'] = df['close'].diff()


      df.to_csv(f'output/{symbol}.csv', index=False)



