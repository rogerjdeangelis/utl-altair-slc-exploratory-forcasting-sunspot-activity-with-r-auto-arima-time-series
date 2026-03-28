# utl-altair-slc-exploratory-forcasting-sunspot-activity-with-r-auto-arima-time-series
Altair scl Exploratory forcasting sunspot activity with r auto arima function time series
    %let pgm=utl-altair-slc-exploratory-forcasting-sunspot-activity-with-r-auto-arima-time-series;

    %stop submission

    Altair scl Exploratory forcasting sunspot activity with r auto arima function time series

    Forecast the next 12 years of sunspots

    Too long to post on a list, see github
    https://github.com/rogerjdeangelis/utl-altair-slc-exploratory-forcasting-sunspot-activity-with-r-auto-arima-time-series

    Altair Community Post
    https://community.altair.com/discussion/55055/i-need-to-try-rapid-miner-with-time-series-forecasting-algorihm-called?tab=all

    REPOS TIME SERIES


    https://github.com/rogerjdeangelis/utl-exploratory-forcasting-sunspot-activity-with-r-auto-arima-time-series
    https://github.com/rogerjdeangelis/utl-impute-missing-values-in-a-arima-timeseries

    https://github.com/rogerjdeangelis/utl-computing-annual-monthly-weekly-and-daily-sums-for-an-irregular-time-series
    https://github.com/rogerjdeangelis/utl-cubic-spline-interpolation-for-missing-values-in-a-time-series-by-group
    https://github.com/rogerjdeangelis/utl-exploratory-forcasting-sunspot-activity-with-r-auto-arima-time-series
    https://github.com/rogerjdeangelis/utl-fill-in-data-between-two-dates-within-by-group-with-non-missing-values-timeseries
    https://github.com/rogerjdeangelis/utl-fill-in-gaps-in-time-series-by-groups
    https://github.com/rogerjdeangelis/utl-fill-in-month-gaps-in-time-series-and-interpolate-missing-values-using-sas-and-r
    https://github.com/rogerjdeangelis/utl-forecast-the-next-four-months-using-a-moving-average-time-series
    https://github.com/rogerjdeangelis/utl-impute-missing-values-in-a-arima-timeseries
    https://github.com/rogerjdeangelis/utl-number-of-shoppers-in-store-every_5-minutes-time-series
    https://github.com/rogerjdeangelis/utl-schdedule-automatic-daily-downloads-of-the-latest-COVID_19-daily-timeseries
    https://github.com/rogerjdeangelis/utl-simple-ascii-plot-to-visually-display-the-the-overlap-of-two-time-series-proc-plot-graph
    https://github.com/rogerjdeangelis/utl-time-series-change-in-university-enrollment-by-year-and-by-year-department-proc-corresp
    https://github.com/rogerjdeangelis/utl-timeseries-calcualtion-of-acf-and-pacf-lagged-autocorrelations
    https://github.com/rogerjdeangelis/utl-timeseries-rolling-three-day-averages-by-county
    https://github.com/rogerjdeangelis/utl-very-simple-arima-timeseries-model-with-forecast-using-drop-down-to-r
    https://github.com/rogerjdeangelis/utl_detecting_structural_breaks_in_a_time_series
    https://github.com/rogerjdeangelis/utl_interpolating_values_in_a_timeseries_when_first-_last_and_middle_values_are_missing
    https://github.com/rogerjdeangelis/utl_javascript_dygraph_graphics_multipanel_time_series
    https://github.com/rogerjdeangelis/utl_moving_average_of_centered_timeseries_or_calculate_a_modified_version_of_moving_averages
    https://github.com/rogerjdeangelis/utl_time_series_analysis_of_sunspots_in_sas_and_r


    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*                  SUNSPOT ACTIVITY  AUTO REGRESSIVE 2 AR(2) MODEL                                                       */
    /*                                                                                                                        */
    /*                                        YEAR                                                                            */
    /*          1970      1980      1990      2000      2010      2020      2030                                              */
    /*         ---+---------+---------+---------+---------+---------+---------+---                                            */
    /*         |                                                                 |                                            */
    /*         |       SUNSPOT ELEVEN YEAR CYCLE (2017-2028 were forcasted)      |                                            */
    /*         |                                                                 |                                            */
    /*         |    Note the downward linear trend is contiued in the forecast   |                                            */
    /*         |                                                                 |                                            */
    /*         |-------------------------------------------------+---------------|                                            */
    /*      15 +                         o-observed              |  p=forcasted  + 15                                         */
    /*         |-------------------------------------------------+---------------|                                            */
    /*         |            |o                                   |               |                                            */
    /*         |            | o      o o                         |               |                                            */
    /*   S     |            |          |                         |               |    S                                       */
    /*   U     |            |         o|         o               | 12 YEAR       |    U                                       */
    /*   N  10 +           oo          |        o|o              | PREDICTION    + 10 N                                       */
    /*   S     |            |          |o      o |               |               |    S                                       */
    /*   P     |            |       o  |         |           o   |    pp         |    P                                       */
    /*   O     |          o |  o       |         | o        |    |   p |p        |    O                                       */
    /*   T     |            |          |      o  |         oo  o |  p  | p       |    T                                       */
    /*   S     |            |   o      | o       |  o       |    | p   |  ppp    |    S                                       */
    /*       5 +            |          |         |   o      |    |     |         +  5                                         */
    /*         |         o  |          |  o      |          |   o|p    |         |                                            */
    /*         |            |    ooo   |   ooo   |    o   o |    p     |         |                                            */
    /*         |        o   |          |         |     ooo  |    |     |         |                                            */
    /*         |            |          |         |          |    |     |         |                                            */
    /*         |            |          |         |          |    |     |         |                                            */
    /*       0 +            |          |         |          |    |     |         +  0                                         */
    /*         |            |          |         |          |    |     | peak    |                                            */
    /*         ---+---------+---------+---------+---------+------+--+---------+---                                            */
    /*          1970      1980      1990      2000      2010      2020      2030                                              */
    /*                                        YEAR                                                                            */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    libname workx sas7bdat "d:/wpswrkx"; /*--- put in autoexec ---*/

    proc datasets lib=workx kill;
    run;quit;

    data workx.yrspots;
      input yer spots @@;
      date = mdy(1, 1, yer);
      format date year4.;
    cards4;
    1976 02.9 1977 04.2 1978 07.6 1979 09.9 1980 09.9
    1981 13.1 1982 12.1 1983 07.6 1984 05.9 1985 03.7
    1986 03.5 1987 03.7 1988 08.4 1989 12.8 1990 11.2
    1991 12.7 1992 08.9 1993 05.8 1994 04.4 1995 03.7
    1996 03.1 1997 03.6 1998 06.6 1999 09.3 2000 10.1
    2001 10.5 2002 09.8 2003 07.1 2004 05.9 2005 04.7
    2006 03.5 2007 02.7 2008 02.5 2009 02.5 2010 03.4
    2011 06.7 2012 06.7 2013 06.9 2014 08.0 2015 06.4
    2016 03.9
    ;;;;
    run;

    /*                   _     _
    (_)_ __  _ __  _   _| |_  | | ___   __ _
    | | `_ \| `_ \| | | | __| | |/ _ \ / _` |
    | | | | | |_) | |_| | |_  | | (_) | (_| |
    |_|_| |_| .__/ \__,_|\__| |_|\___/ \__, |
            |_|                        |___/
    */

    1                                          Altair SLC        16:28 Saturday, March 28, 2026

    NOTE: Copyright 2002-2025 World Programming, an Altair Company
    NOTE: Altair SLC 2026 (05.26.01.00.000758)
          Licensed to Roger DeAngelis
    NOTE: This session is executing on the X64_WIN11PRO platform and is running in 64 bit mode

    NOTE: AUTOEXEC processing beginning; file is C:\wpsoto\autoexec.sas
    NOTE: AUTOEXEC source line
    1       +  ï»¿ods _all_ close;
               ^
    ERROR: Expected a statement keyword : found "?"

    NOTE: AUTOEXEC processing completed

    1         libname workx sas7bdat "d:/wpswrkx"; /*--- put in autoexec ---*/
    NOTE: Library workx assigned as follows:
          Engine:        SAS7BDAT
          Physical Name: d:\wpswrkx


    Altair SLC

    The DATASETS Procedure

             Directory

    Libref           WORKX
    Engine           SAS7BDAT
    Physical Name    d:\wpswrkx
    2
    3         proc datasets lib=workx kill;
    NOTE: No matching members in directory
    4         run;quit;
    NOTE: Procedure datasets step took :
          real time : 0.015
          cpu time  : 0.000


    5
    6         data workx.yrspots;
    7           input yer spots @@;
    8           date = mdy(1, 1, yer);
    9           format date year4.;
    10        cards4;

    NOTE: A new line was read when INPUT statement read past the end of a line
    NOTE: Data set "WORKX.yrspots" has 41 observation(s) and 3 variable(s)
    NOTE: The data step took :
          real time : 0.000
          cpu time  : 0.015


    11        1976 02.9 1977 04.2 1978 07.6 1979 09.9 1980 09.9
    12        1981 13.1 1982 12.1 1983 07.6 1984 05.9 1985 03.7
    13        1986 03.5 1987 03.7 1988 08.4 1989 12.8 1990 11.2
    14        1991 12.7 1992 08.9 1993 05.8 1994 04.4 1995 03.7
    15        1996 03.1 1997 03.6 1998 06.6 1999 09.3 2000 10.1
    16        2001 10.5 2002 09.8 2003 07.1 2004 05.9 2005 04.7
    17        2006 03.5 2007 02.7 2008 02.5 2009 02.5 2010 03.4
    18        2011 06.7 2012 06.7 2013 06.9 2014 08.0 2015 06.4
    19        2016 03.9
    20        ;;;;
    21        run;


    ERROR: Error printed on page 1

    NOTE: Submitted statements took :
          real time : 0.143
          cpu time  : 0.062

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    proc arima data=workx.yrspots;
        identify var=spots;
        estimate p=2 method=ml;
        forecast lead=12 id=date interval=year out=workx.forecast_results;
        title "AR(2) Model Forecast for 2017-2028";
    run;

    data workx.forecast;
      set workx.forecast_results;
      /*--- get numeric year from sas date ---*/
      date=input(put(date,year4.),4.);
      /*--- create single column with observed and predicted values ---*/
      if missing(spots) then do; spots=forecast; source="PREDICTED";end;
      else source="OBSERVED";
      keep date spots source;
    run;quit;

    options ls=64 ps=32;
    proc plot data=workx.forecast ;
    plot spots*date='*'/
              box
              vaxis=0 to 15 by 5
              haxis=1970 to 2030 by 10;
    run;quit;


    /**************************************************************************************************************************/
    /* WORKX.FORECAST total obs=53                                                                                            */
    /*                                                                                                                        */
    /* DATE     SPOTS     SOURCE                     SUNSPOT ACTIVITY  AUTO REGRESSIVE 2 AR(2) MODEL                          */
    /*                                                                                                                        */
    /* 1976     2.9000   OBSERVED                                          YEAR                                               */
    /* 1977     4.2000   OBSERVED            1970      1980      1990      2000      2010      2020      2030                 */
    /* 1978     7.6000   OBSERVED           ---+---------+---------+---------+---------+---------+---------+---               */
    /* 1979     9.9000   OBSERVED           |                                                                 |               */
    /* 1980     9.9000   OBSERVED           |       SUNSPOT ELEVEN YEAR CYCLE (2017-2028 were forcasted)      |               */
    /* 1981    13.1000   OBSERVED           |                                                                 |               */
    /* 1982    12.1000   OBSERVED           |    Note the downward linear trend is contiued in the forecast   |               */
    /* 1983     7.6000   OBSERVED           |                                                                 |               */
    /* 1984     5.9000   OBSERVED           |-------------------------------------------------+---------------|               */
    /* 1985     3.7000   OBSERVED        15 +                         o-observed              |  p=forcasted  + 15            */
    /* 1986     3.5000   OBSERVED           |-------------------------------------------------+---------------|               */
    /* 1987     3.7000   OBSERVED           |            |o                                   |               |               */
    /* 1988     8.4000   OBSERVED           |            | o      o o                         |               |               */
    /* 1989    12.8000   OBSERVED     S     |            |          |                         |               |    S          */
    /* 1990    11.2000   OBSERVED     U     |            |         o|         o               |               |    U          */
    /* 1991    12.7000   OBSERVED     N  10 +           oo          |        o|o              | PREDICTED     + 10 N          */
    /* 1992     8.9000   OBSERVED     S     |            |          |o      o |               |               |    S          */
    /* 1993     5.8000   OBSERVED     P     |            |       o  |         |           o   |    pp         |    P          */
    /* 1994     4.4000   OBSERVED     O     |          o |  o       |         | o        |    |   p |p        |    O          */
    /* 1995     3.7000   OBSERVED     T     |            |          |      o  |         oo  o |  p  | p       |    T          */
    /* 1996     3.1000   OBSERVED     S     |            |   o      | o       |  o       |    | p   |  ppp    |    S          */
    /* 1997     3.6000   OBSERVED         5 +            |          |         |   o      |    |     |         +  5            */
    /* 1998     6.6000   OBSERVED           |         o  |          |  o      |          |   o|p    |         |               */
    /* 1999     9.3000   OBSERVED           |            |    ooo   |   ooo   |    o   o |    p     |         |               */
    /* 2000    10.1000   OBSERVED           |        o   |          |         |     ooo  |    |     |         |               */
    /* 2001    10.5000   OBSERVED           |            |          |         |          |    |     |         |               */
    /* 2002     9.8000   OBSERVED           |            |          |         |          |    |     |         |               */
    /* 2003     7.1000   OBSERVED         0 +            |          |         |          |    |     |         +  0            */
    /* 2004     5.9000   OBSERVED           |            |          |         |          |    |     |         |               */
    /* 2005     4.7000   OBSERVED           ---+---------+---------+---------+---------+------+--+---------+---               */
    /* 2006     3.5000   OBSERVED            1970      1980      1990      2000      2010      2020      2030                 */
    /* 2007     2.7000   OBSERVED                                          YEAR                                               */
    /* 2008     2.5000   OBSERVED                                                                                             */
    /* 2009     2.5000   OBSERVED                                                                                             */
    /* 2010     3.4000   OBSERVED                                                                                             */
    /* 2011     6.7000   OBSERVED                                                                                             */
    /* 2012     6.7000   OBSERVED                                                                                             */
    /* 2013     6.9000   OBSERVED                                                                                             */
    /* 2014     8.0000   OBSERVED                                                                                             */
    /* 2015     6.4000   OBSERVED                                                                                             */
    /* 2016     3.9000   OBSERVED                                                                                             */
    /*                                                                                                                        */
    /* 2017     3.3745   PREDICTED                                                                                            */
    /* 2018     4.1804   PREDICTED                                                                                            */
    /* 2019     5.4774   PREDICTED                                                                                            */
    /* 2020     6.6053   PREDICTED                                                                                            */
    /* 2021     7.2397   PREDICTED                                                                                            */
    /* 2022     7.3651   PREDICTED                                                                                            */
    /* 2023     7.1508   PREDICTED                                                                                            */
    /* 2024     6.8142   PREDICTED                                                                                            */
    /* 2025     6.5245   PREDICTED                                                                                            */
    /* 2026     6.3636   PREDICTED                                                                                            */
    /* 2027     6.3339   PREDICTED                                                                                            */
    /* 2028     6.3908   PREDICTED                                                                                            */
    /**************************************************************************************************************************/

    /*                                   _
     _ __  _ __ ___   ___ ___  ___ ___  | | ___   __ _
    | `_ \| `__/ _ \ / __/ _ \/ __/ __| | |/ _ \ / _` |
    | |_) | | | (_) | (_|  __/\__ \__ \ | | (_) | (_| |
    | .__/|_|  \___/ \___\___||___/___/ |_|\___/ \__, |
    |_|                                          |___/
    */

    1                                          Altair SLC        16:30 Saturday, March 28, 2026

    NOTE: Copyright 2002-2025 World Programming, an Altair Company
    NOTE: Altair SLC 2026 (05.26.01.00.000758)
          Licensed to Roger DeAngelis
    NOTE: This session is executing on the X64_WIN11PRO platform and is running in 64 bit mode

    NOTE: AUTOEXEC processing beginning; file is C:\wpsoto\autoexec.sas
    NOTE: AUTOEXEC source line
    1       +  ï»¿ods _all_ close;
               ^
    ERROR: Expected a statement keyword : found "?"

    NOTE: AUTOEXEC processing completed

    1         proc arima data=workx.yrspots;
                              ^
    ERROR: Data set "WORKX.yrspots" not found
    2             identify var=spots;
    3             estimate p=2 method=ml;
    4             forecast lead=12 id=date interval=year out=workx.forecast_results;
    5             title "AR(2) Model Forecast for 2017-2028";
    NOTE: Procedure ARIMA was not executed because of errors detected
    6         run;
    NOTE: Procedure arima step took :
          real time : 0.000
          cpu time  : 0.000


    7
    8         data workx.forecast;
    9           set workx.forecast_results;
                    ^
    ERROR: Data set "WORKX.forecast_results" not found
    10          /*--- get numeric year from sas date ---*/
    11          date=input(put(date,year4.),4.);
    12          /*--- create single column with observed and predicted values ---*/
    13          if missing(spots) then do; spots=forecast; source="PREDICTED";end;
    14          else source="OBSERVED";
    15          keep date spots source;
    16        run;

    NOTE: DATA step was not executed because of errors detected
    NOTE: The data step took :
          real time : 0.000
          cpu time  : 0.000


    16      !     quit;
    17
    18        options ls=64 ps=32;
    19        proc plot data=workx.forecast ;
                             ^
    ERROR: Data set "WORKX.forecast" not found
    20        plot spots*date='*'/
    21                  box
    22                  vaxis=0 to 15 by 5
    23                  haxis=1970 to 2030 by 10;
    NOTE: Procedure PLOT was not executed because of errors detected
    24        run;
    NOTE: Procedure plot step took :
          real time : 0.000
          cpu time  : 0.000


    24      !     quit;
    25
    ERROR: Error printed on page 1

    NOTE: Submitted statements took :
          real time : 0.079
          cpu time  : 0.062
    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
