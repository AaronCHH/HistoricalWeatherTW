.. sectnum::

HistoricalWeatherTW 台灣歷史天氣爬蟲
==============================================

Data from `觀測資料查詢系統 <http://e-service.cwb.gov.tw/HistoryDataQuery/>`_

Usage
============
This script is to crawl the information of `觀測資料查詢 <https://e-service.cwb.gov.tw/HistoryDataQuery/index.jsp>`_ website

run the following of ``collect_weather_tw`` you will see the result!

.. code-block:: python

    def collect_weather_tw(station_csv_path: Path, output_path,
                           end_date: datetime.date, begin_date: datetime.date,
                           query_format,
                           convert2num):

**You can refer to ``__init__.py`` for more help**

QUICKLY START
---------------

.. code-block:: python

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

.. note:: station.csv (you can find it from the https://e-service.cwb.gov.tw/wdps/obs/state.htm)

Data 資料
=============

資料會以觀測站ID+站名儲存

.. note:: There have some non-numeric forms of the original data.
    Such as indefinite wind direction V, rain track T, etc. the variable of ``CONVERT2NUM`` will replace them with numbers.

資料欄位如下
--------------------

`ObsTime` 觀測時間(LST) 

`StnPres` 測站氣壓(hPa) 

`SeaPres`	海平面氣壓(hPa)

`Temperature` 氣溫(℃)

`Tddewpoint` 露點溫度(℃)

`RH` 相對溼度(%)

`WS` 風速(m/s)

`WD` 風向(360degree)

`WSGust` 最大陣風(m/s)

`WDGust` 最大陣風風向(360degree)

`Precp` 降水量(mm)

`PrecpHour` 降水時數(hr)

`SunShine` 日照時數(hr)

`GloblRad` 全天空日射量(MJ/㎡)

`Visb` 能見度(km)

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
