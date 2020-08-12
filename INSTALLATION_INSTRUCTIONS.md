Installing A New Precise Model Into Mycroft Core

A Precise model is composed of two files. The model.pb file and the model.pb.params file. They may live anywhere on the file system since their exact location is controlled via the mycroft.conf config file, however, by default Mycroft installs the model in your home directory at ~/.mycroft/precise.

It is usually best to leave that model alone and store your model somewhere else. The only thing to keep in mind is that both the .pb and the .pb.params files must exist in the same directory.

The 'original' directory in this branch holds the initial .pb and .pb.params files which are installed by default by Mycroft Core. They should match the model found in your home directory at ~/.mycroft/precise. Other directories hold newer models. To test one simply download it to your computer then update your mycroft.conf file. Assuming you downloaded the .pb and .pb.params file from hey-mycroft-001/ to your local /tmp directory (BOTH ARE REQUIRED!) you would edit your mycroft.conf file under the hot words section for the wake word 'hey mycroft' as follows ...

"local_model_file": "/tmp/hey-mycroft_C1_E6000_B5000_D0.2_R20_S0.8.pb"

//"local_model_file": "~/.mycroft/precise/hey-mycroft.pb",

"sensitivity": 0.1,

"trigger_level":7

Here we have commented out the line that points to the old hey-mycroft.pb file and added a new line that points to our new model.  The sensitivity value is a float and ranges between 0.0 - 1.0 with sensitivity increasing as the value increases. A value of 0.1 will minimize false positives while a value of 0.9 will recognize almost anything.

The trigger level relates to consecutive positive samples and is an integer between  1 - infinity with practical values ranging betwen 1 and 10. The higher the value the less likely a false positive will trigger an activation, however, high values also cause the recognizer to produce more false negatives (IE does not activate when it should).  

The default values for these two parameters is 0.5 for sensitivity and 3 for trigger level. Once you change these values you must restart Mycroft.
  
