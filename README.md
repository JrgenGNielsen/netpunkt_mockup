Netpunkt Mockup:

Module to record & replay webservice responses that are queried through 
TingClient.

Uses TingClient's cache key to name files, and identify canned responses.

When running an automated test, it is nessecary to have known responses to a 
query - live webservices may change or be inaccessible. 

The idea is to have a module that, when enabled, bypass TingClient's cache
function and make TingClient return a recorded response from Netpunkt Mockup,
if the cache key is found in Netpunkt Mockup's data.

In the administration part of Netpunkt Mockup is a switch, that toggle the state of
Netpunkt Mockup: record or replay. If recording, Netpunkt Mockup saves all responses 
that go through TingClient, using the cache key as file name. 

If using drush to toggle recording on/off:
$ drush vset netpunkt_mockup_recording [1|0]

So: When writing a new test, or updating an old, set file permissions on the 
cache folder, activate recording in the Netpunkt Mockup, and run the tests. 
Then commit the updates in the Netpunkt Mockup cache folder.

When the automated tests are run, enable the Netpunkt Mockup module, and the 
TingClient responses will return cached results from Netpunkt Mockup.