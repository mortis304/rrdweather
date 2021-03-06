# RRDWeather

Released under the GNU General Public License  
http://www.wains.be/projects/rrdweather/


#### What is RRDWeather ?

RRDWeather is a set of scripts working with RRDtool and weather.com.
It collects weather info from the web on a regular basis and puts it in RRDtool graphs.


#### Installation

See INSTALL


#### Contributors

- Heikki Hokkanen
- Lionel Porcheron
- Gregory Bittan
- Gregory Guthrie


#### Changelog

Version 0.42 - November 2007 :

- weather.cgi
  * added one "if" to suppress warnings when creating last set of graphs (Heikki Hokkanen)
  * if the GET parameter 'zip' is not provided, use the first ZIP code found in /etc/rrdweather.conf (Heikki Hokkanen)
  * when clicking on the yearly graphs, you are now redirected to daily graphs (Sebastien Wains) 
  * cities monitored selectable from a drop-down list (Sebastien Wains)
- rrdweather.conf
  * VERSION variable


Version 0.42 - October 2007 :

- weather.cgi 
  * header titles now link to their section. (Heikki Hokkanen)
  * click on graphs to go to the next section (click on daily graphs to reach weekly graphs and so on)
  * no longer necessary to have several weather.cgi files to display different cities, zip passed as argument. Idea by Gregory Guthrie
  * city name fetched from the XML source
  * made XHTML 1.1 and CSS 2.1 compliant (again)


Version 0.41 - October 2007 :

- applied the patches made available by Lionel Porcheron in Ubuntu Universe repository
  * configuration file in /etc instead of editing script files
  * remove interactions and read informations from configuration file
  * change database location in cgi script
  * db_builder.sh and db_update.sh scripts now go in /usr/share/rrdweather
    and no more in /usr/lib/rrdweather
  * call rrdweather_cron.sh which creates rrd database if necessary (no need to run db_builder.sh first)
- lower and upper limit variables for pressure graphs in cgi script
- speed variable for wind graphs in cgi script 
- reduced size of graphs and changed general layout of graph page
- removed the average label for pressure, which was kind of pointless, and due to the smaller graphs, 
  the labels for pressure were too large, so I needed to get rid of one
- new install script


Version 0.40 - December 2006 :

- Gregory Bittan <gregory.bittan@gmail.com> reported an issue when the web connection is down.
  The script would still feed the RRD databases with a value of 0, messing up the average figures.
- The update script can now handle the monitoring of several cities
- Lionel Porcheron <lionel@alveonet.org> made RRDweather available to the Ubuntu Community trough
  the Universe repository
- To achieve the goal of monitoring several cities from a single script, RRDWeather had to use
  a new directory structure in order to store database files
- Better indenting
- Improved bash code
- Improved debugging mode
- ...


Version 0.36 - January 2006:

- Lionel Porcheron <lionel@alveonet.org> made weather.cgi fully w3c XHTML 1.1 et CSS 2.1 compliant
