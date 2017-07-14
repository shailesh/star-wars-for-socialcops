#Clone Wars 2.0
--------------

Prime Minister Lama Su,

I hope this letter finds you in the best of health.

The last batch of clones you built for us were faulty
and did not perform as expected (https://www.youtube.com/watch?v=b0DuUnhGBK4)

We unearthed some secrets about how the droid army was trained and hope that
you can use this information to make a better army this time around. With the
galaxy on the brink of another war, I cannot help but emphasize how much a 
large discount will help the Republic in its efforts.

One of our allies came across these schematics in an abandoned base that shed some
light on the droid training exercises, master Yoda concluded that a pair of droids
undergo various kinds of battle simulations during which each droid records its
progress and learning in a force, currently unfamilair to us, called "Data".
This force from both droids is then combined in a ritual called the
"Sync" resulting in both droids having an increased data force.

Please have a look at this schematic, your engineers may have better luck
decoding its mysteries.

            +----------------+                +----------------+
            |                |                |                |
            |   +--------+   |      Sync      |   +--------+   |
            |   |-|Data|-|   | +------------> |   |-|Data|-|   |
            |   +--------+   | <------------+ |   +--------+   |
            |                |                |                |
            |    Driod  A    |                |    Driod  B    |
            |                |                |                |
            +----------------+                +----------------+

May the force be with you.

- Sifo-Dyas


[....2 months later....]


Prime Minister Lama Su!,

I hope the army is coming along nicely. The force has given us more clarity in
the last few months. As it turns out, this "Data" that we were so worried about,
is just a method by which the droids store information about their experiences and
orders. Most importantly, the "Sync" ritual was just an exchange of files
from one droid to another in both directions. This is how their data force
increased after the ritual.

Master Windoo has been doing extensive research and has come up with a simplified
experiment to test if this training method can be implemented. He says that you
should start by figuring out how to synchronize data between a folder on one
device (say device A) and a folder on another device (say device B).
In addition to that, a change made to the data on one device should also be made 
available to the other device as well. If we have a way to do this then we could 
potentially improve the quality of the new clone army. I hope your engineers
are able to make sense of all of this information. Do write back to me if you
need more information.

Please share your method and implementation in great detail with us so
that it can be added to our records in the Jedi Temple. I wish you luck.

May the force be with you.

- Sifo-Dyas

```
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
             |  #  |#  |   B-SD3 Security Droid
          LS |  #  |#  |      - Front View -


```
#Setting Up and Usage:

1. Create a API on dropbox and set the authorization token in the config.py file.

2. Set the local directory on your pc that you want to sync with folders of other devices.

3. We will set up a cron job for the file fileDownload.py on our system. A cron job can be set up on Ubuntu by the following commands.
  **crontab -e**  
  
  Append the below line to the file with the appropriate path to the file.   

  */2 * * * * /usr/bin/python /home/arpan/gitProjects/FolderSync/fileDownload.py  
   
   This enables us to run the script fileDownload.py every 2 mins where the script iterates through the files on dropbox client and downloads the
   necessary files onto our system.  

4. Run the file fileUpload.py in the background as a daemon. This script watches the folder that we specified in the config.py file as 
  LOCAL_DIRECTORY_WATCH and fires an event whenever the specified folder undergoes any modification. The modified file is pushed to dropbox.

#Installation and Dependencies

**sudo pip install dropbox**   
**sudo pip install watchdog**


#Additional Considerations

You might get the following warning on running the scripts

/usr/local/lib/python2.7/dist-packages/requests/packages/urllib3/util/ssl_.py:318: SNIMissingWarning: An HTTPS request has been made, but the SNI (Subject Name Indication) extension to TLS is not available on this platform. This may cause the server to present an incorrect TLS certificate, which can cause validation failures. You can upgrade to a newer version of Python to solve this. For more information, see https://urllib3.readthedocs.io/en/latest/security.html#snimissingwarning.
  SNIMissingWarning


Refer to the below stackoverflow link and install the dependencies to solve the warning.

http://stackoverflow.com/questions/29134512/insecureplatformwarning-a-true-sslcontext-object-is-not-available-this-prevent
