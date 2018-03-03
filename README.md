# general_info


#!/usr/bin/env python3
import re
import sys


"""  Just a general idea, for actions done by pronk
      the real thing would be different, but this
      script is for independant, local CLI use.
"""



###  Use -d as a CLI argument, to have the argument list printed.  (used for a little debugging)
if " -d" in sys.argv:
  print(sys.argv)  # debug





###  Function to tell usage.
def usFunc():
  exit("usage: {} ?kill <person's name>".format(sys.argv[0]))


###  Try to set the variables.
try:
  kill_var = sys.argv[1]
  pers_var = sys.argv[2]
  both_var = kill_var + " " + pers_var
except:
  usFunc()


###  Pretend to be like pronk's dict lol.
reply = dict()
reply["{} {}".format(kill_var, pers_var)]  =  "Immediately, pronk kills {}!".format(pers_var)


###  Printing responses.
if kill_var == "?kill":
  if re.match("pronk", pers_var, flags=re.I):				# Check for the "pronk" string here, with regex; in any case.
    print(reply[both_var].replace(pers_var, pers_var.lower()))		# Use .replace() to properly use the pronk name, in lower case.
    print("Long live {}!!".format(pers_var.lower()))
  else:
    print(reply[both_var])
    print("{} is dead.".format(pers_var))
else:
  usFunc()
