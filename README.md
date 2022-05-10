How to setup local apache server to host websites(Windows&Linux).

Windows

The end result will be 3 ports open which will serve websites, each one in a diffrent way

1.Download the XAMMP .msi executable from 
https://www.apachefriends.org/download.html

For this tutorial i am using  8.0.18 version

2.Run the .msi file and click next on all to use the default configuration

3.after installation run the XAMMP program. In XAMMP click on config in "Apache" row and select "Apache(htttpd.conf)"
or go to C:\xampp\apache\conf\htttpd.conf

in the config file add the following lines :

#Opens ports to listen to
Listen 90
Listen 1008
Listen 8080

#configure root directory to allow serving content 
DocumentRoot "C:/servakas" # root of the served webpage, specified permmisions here will apply to all child directories
<Directory "C:/servakas">
	Options Indexes FollowSymLinks # allow indexing of directories
	Require all granted # allow everyone
</Directory>

4.in the specified directory add two directories each with at least index.html file with content.


5.go to httpd-vhosts.conf file in C:\xampp\apache\conf\extra\
and add these lines at the bottom to bind what port serves what directory:

<VirtualHost localhost:1008> #domain by which it is called through browser
    DocumentRoot "C:/btc" # root of direcotry
    ServerName localhost
	<Directory "C:/btc"> # directory
		Require all granted # allow everyone
    </Directory>
</VirtualHost>

<VirtualHost 192.168.8.106:8080>
    DocumentRoot "C:/vaporwawe"
    ServerName 192.168.8.106
	<Directory "C:/vaporwawe">
		AllowOverride All
		<Files ".tra"> # block access to view contents of file ".tra"
			Require all denied
		</Files>
    </Directory>
</VirtualHost>

6.Add index.html files to these directories 
in the C:/vaporwawe direcotry create ".tra" (leave it empty) and ".htaccess" file and add these lines:

AuthType Basic  # authentication type
AuthName "Čia apipėlšimas, įrašykite savo admin prisijungimo duomenis žemiau:" #prompt for user
AuthBasicProvider file # type of credential storage
AuthUserFile "C:/passwords/.htpasswd" # credential location
Require valid-user # authenticate only valid users


7.create a file in C:/passwords/ called ".htpasswd" and add these lines:

adminas:adminas123

8.After the configuration is done go to XAMMP application and click in "Apache" row "Start"

9.Explore and test the websites at:
localhost:90
localhost:1008
192.168.8.106:8080 # enter the credentials specified in the .htpasswd file

example:

ping localhost:90
curl localhost:90

9.view activity and error logs in C:\xampp\apache\logs

Linux

The end result will be a single site running listening on port 80

1.run:

apt-get update
apt-get install apache2


2.add a website catalog under:

/var/www/html/

3.give it correct permmisions:

chown -R www-data:www-data /var/www/html/directory-name/


4.create configuration file for virtual host:

/etc/apache2/sites-available/yourdomain.com.conf


and add the lines below

<VirtualHost *:80>
    ServerAdmin admin@yourdomain.com
    ServerName yourdomain.com
    DocumentRoot /var/www/html/directory-name
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


5.and then this to enable virtual host:

a2ensite yourdomain.com.conf 


and restart:
 
service apache2 reload 


You can repeat the steps from 2 to 5 to add multiple sites