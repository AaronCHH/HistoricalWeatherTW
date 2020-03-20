.. sectnum::

.. raw:: html

    <p align="left">

        <a href="https://pypi.org/project/carson-tool.HistoricalWeatherTW/">
        <img src="https://img.shields.io/static/v1?&style=plastic&logo=pypi&label=App&message=HistoricalWeather&color=00FFFF"/></a>

        <a href="https://pypi.org/project/carson-tool.HistoricalWeatherTW/">
        <img src="https://img.shields.io/pypi/v/carson-tool.HistoricalWeatherTW.svg?&style=plastic&logo=pypi&color=00FFFF"/></a>

        <a href="https://pypi.org/project/carson-tool.HistoricalWeatherTW/">
        <img src="https://img.shields.io/pypi/pyversions/carson-tool.HistoricalWeatherTW.svg?&style=plastic&logo=pypi&color=00FFFF"/></a>

        <a href="https://github.com/CarsonSlovoka/HistoricalWeatherTW/blob/master/LICENSE">
        <img src="https://img.shields.io/pypi/l/carson-tool.HistoricalWeatherTW.svg?&style=plastic&logo=pypi&color=00FFFF"/></a>

        <br>

        <a href="https://github.com/CarsonSlovoka/HistoricalWeatherTW">
        <img src="https://img.shields.io/github/last-commit/CarsonSlovoka/HistoricalWeatherTW?&style=plastic&logo=github&color=00FF00"/></a>

        <img src="https://img.shields.io/github/commit-activity/y/CarsonSlovoka/HistoricalWeatherTW?&style=plastic&logo=github&color=0000FF"/></a>

        <a href="https://github.com/CarsonSlovoka/HistoricalWeatherTW">
        <img src="https://img.shields.io/github/contributors/CarsonSlovoka/HistoricalWeatherTW?&style=plastic&logo=github&color=111111"/></a>

        <a href="https://github.com/CarsonSlovoka/HistoricalWeatherTW">
        <img src="https://img.shields.io/github/repo-size/CarsonSlovoka/HistoricalWeatherTW?&style=plastic&logo=github"/></a>

        <br>

        <a href="https://pepy.tech/project/carson-tool-historicalweathertw">
        <img src="https://pepy.tech/badge/carson-tool-historicalweathertw"/></a>

        <a href="https://pepy.tech/project/carson-tool-historicalweathertw/month">
        <img src="https://pepy.tech/badge/carson-tool-historicalweathertw/month"/></a>

        <a href="https://pepy.tech/project/carson-tool-historicalweathertw/week">
        <img src="https://pepy.tech/badge/carson-tool-historicalweathertw/week"/></a>

        <!--
            <img src="https://img.shields.io/github/commits-since/m/CarsonSlovoka/HistoricalWeatherTW/Dev?label=commits%20to%20be%20deployed"/></a>
        -->

    </p>

HistoricalWeatherTW 台灣歷史天氣爬蟲
==============================================

This script is to crawl the information of `觀測資料查詢 <https://e-service.cwb.gov.tw/HistoryDataQuery/index.jsp>`_ website

Data from `觀測資料查詢系統 <http://e-service.cwb.gov.tw/HistoryDataQuery/>`_

Usage
============

#. Prepare `station.csv`_.

    .. note:: station.csv (you can find it from the https://e-service.cwb.gov.tw/wdps/obs/state.htm)

#. run the function of ``collect_weather_tw`` you will see the result!

    .. code-block:: python

        def collect_weather_tw(station_csv_path: Path, output_path,
                               end_date: datetime.date, begin_date: datetime.date,
                               query_format,
                               convert2num):

**You can refer to** `__init__.py`_ **for more help**

    1. Prepare `config.yaml`_ and use this path as input parameter
    #. run `__init__.py`_

QUICKLY START
---------------

.. code-block:: python

    from Carson.Tool.HistoricalWeatherTW import collect_weather_tw, QueryFormat
    from pathlib import Path
    import datetime
    import os

    if __name__ == '__main__':
        STATION_CSV = '../config/CSV/station_test.csv'
        OUTPUT_PATH = Path(f'../temp/year_result.csv')
        BEGIN_DATE = datetime.date(2019, 10, 1)
        END_DATE = datetime.date(2019, 10, 2)
        QUERY_FORMAT = QueryFormat.DAY
        CONVERT2NUM = True
        collect_weather_tw(Path(STATION_CSV), OUTPUT_PATH,
                           BEGIN_DATE, END_DATE,
                           QUERY_FORMAT,
                           CONVERT2NUM)
        os.startfile(OUTPUT_PATH)



Data
================

The output depends on ``QueryFormat``!

.. csv-table:: Day
   :file: test/output/day.csv
   :header-rows: 1

.. csv-table:: MONTH
   :file: test/output/month.csv
   :header-rows: 1

.. csv-table:: YEAR
   :file: test/output/year.csv
   :header-rows: 1

.. note:: There have some non-numeric forms of the original data.
    Such as indefinite wind direction V, rain track T, etc. the variable of ``CONVERT2NUM`` will replace them with numbers.

Release note
======================

v4.0
---------
    Encapsulated as API

v3.0
---------
Features:

    - All outputs into a single file. (making it easier to use for SQL)
    - The output header field will automatically grab the content on the web page (not use hard coding)
    - You can choose the type of query (year, month, day) according to your needs.

Other:

    - Make the code easier to read.

V2.0
-------

加入全台觀測站

V1.0
---------
第一版

.. _`__init__.py`: https://github.com/CarsonSlovoka/HistoricalWeatherTW/blob/master/Carson/Tool/HistoricalWeatherTW/__init__.py#L15-L33
.. _`config.yaml`: https://github.com/CarsonSlovoka/HistoricalWeatherTW/blob/master/Carson/Tool/HistoricalWeatherTW/config/config.yaml
.. _`station.csv`: https://github.com/CarsonSlovoka/HistoricalWeatherTW/blob/master/Carson/Tool/HistoricalWeatherTW/config/CSV/station.csv
