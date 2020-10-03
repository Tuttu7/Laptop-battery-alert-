###Bash script to check the battery usage of the laptop and alert if it is below 10 %
####################################################################################

#!/bin/bash

battery=`acpi -b | grep -P -o '[0-9]+(?=%)'`

if [ $battery -le 95 ]
then

  (speaker-test -t sine -f 1000)&pid=$! ; sleep .9s ; kill -9 $pid
  notify-send "Battery low" "The battery usage is $battery % !!"
  (speaker-test -t sine -f 1000)&pid=$! ; sleep .9s ; kill -9 $pid

fi
