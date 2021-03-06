# RRDWeather

Released under the GNU General Public License  
http://www.wains.be/projects/rrdweather/


What do I need ?

- a linux or unix machine running 24/7
- awk, sed and wget
- apache webserver allowing ExecCGI (or any other webserver)
- rrdtool >= 1.2.0
- the following perl libraries : 
    * RRDs
    * POSIX 
    * perl::XML::Simple
    * perl::XML::Parser
    * perl::Config::File


Installation steps

- if you want to monitor cities outside of the USA, find the international city code by searching on weather.com
  By searching for "Mons, Belgium" I'm pointed to this URL : http://www.weather.com/weather/local/BEXX0014?from=search_city
  The international city code is BEXX0014.

- "untar-gz" the files to a temporary directory 

- edit files/rrdweather.conf to fit the locations you want to monitor, your needs and configuration
  edit files/rrdweather_cron and change the user that must run the script (by default www-data under Debian, apache under RedHat)

- execute install.sh as root, this will copy the config file, cron file and scripts to default locations 
  As soon as the files have been copied, the cron will start doing its job and the RRD databases will start being populated

- copy "weather.cgi" to a cgi-bin folder of your webserver.

- after a few minutes, you should see graphs at http://yourdomain.tld/cgi-bin/weather.cgi?zip=BEXX0014


Troubleshooting

Q : I get a blank page when trying to reach weather.cgi in my web browser
    OR I get something like this in the error logs of Apache

    Can't locate RRDs.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/cgi-bin/weather.cgi line 7.

A : You will probably need to install the missing perl library

    Under Debian systems : 
    # apt-get install librrds-perl

    Under RedHat systems :
    You will need to install the package "perl-rrdtool" provided by several 3rd party repositories.
    Search for "perl-rrdtool RPM" in Google.

    Or build from sources.


Q : I can reach weather.cgi but no graph is displayed !

A : check the permissions on :

- the database directory : directory reachable by your web server ?
- the database files must be owned by the web server user/group and writable by the web server.
- the temporary directory and its files. These should be owned by the web server user/group.


Q : What if I don't pass the zip as argument (weather.cgi?zip=BEXX0014) but simply call weather.cgi ?

A : RRDWeather will pull the first zip specified under /etc/rrdweather.conf
    You may want to specify your "favorite" zip code first
