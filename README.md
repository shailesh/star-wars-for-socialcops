									 +---------------------+
									 | Whats going on here?|
									 +------------------+--+
											    |
											    |
					  _                                                 |
					  \\                                                |
					   \\_          _.-._                               |
					    X:\        (_/ \_)     <------------------------+
					    \::\       ( ==  )
					     \::\       \== /
					    /X:::\   .-./`-'\.--.
					    \\/\::\ / /     (    l
					     ~\ \::\ /      `.   L.
					       \/:::|         `.'  `
					       /:/\:|          (    `.
					       \/`-'`.          >    )
						      \       //  .-'
						       |     /(  .'
						       `-..-'_ \  \
						       __||/_ \ `-'
						      / _ \ #  |
						     |  #  |#  |
						     |  #  |#  | 

#Setting Up and Usage:

1. Create a API on dropbox and set the authorization token in the config.py file.

2. Set the local directory on your pc that you want to sync with folders of other devices.

3. We will set up a cron job for the file fileDownload.py on our system. A cron job can be set up on Ubuntu by the following commands.
  **crontab -e**
  
  Append the below line to the file with the appropriate path to the file.

  */2 * * * * /usr/bin/python /home/shailesh/Documents/socialcops/fileDownload.py
   
   This enables us to run the script fileDownload.py every 2 mins where the script iterates through the files on dropbox client and downloads the
   necessary files onto our system.

4. Run the file fileUpload.py in the background as a daemon. This script watches the folder that we specified in the config.py file as 
  LOCAL_DIRECTORY_WATCH and fires an event whenever the specified folder undergoes any modification. The modified file is pushed to dropbox.

#Installation and Dependencies

**sudo pip install dropbox**

**sudo pip install watchdog**
