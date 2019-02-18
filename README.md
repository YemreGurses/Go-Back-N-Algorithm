# Description

Go-Back-N algorithm implementation of pipelined reliable data transfer in python language.
Simply transfers input.txt from source.py to dest.py by passing through broker.py.
Every script writes its own txt file. Therefore, file of the script is created in the directory of that script. 
It's implemented for running on local machine. Easily, can be used for remote machines by just changing IP addresses.
Used 'datetime' library to calculate difference time.

# TO RUN
Run the python scripts in the following orders: broker.py, dest.py, source.py

# Routing commands

sudo route add -host "IP" gw "IP"
sudo route add -host "IP" gw "IP"

# loss
## broker
sudo tc qdisc change dev eth3 root netem loss 0.5% corrupt 0% duplicate 0% delay 3 reorder 0% 0%
## r1
sudo tc qdisc change dev eth1 root netem loss 0.5% corrupt 0% duplicate 0% delay 3 reorder 0% 0%
## dest
sudo tc qdisc change dev eth2 root netem loss 0.5% corrupt 0% duplicate 0% delay 3 reorder 0% 0%

#corruption
## broker
sudo tc qdisc change dev eth3 root netem loss 0% corrupt 0.2% duplicate 0% delay 3 reorder 0% 0%
## r1
sudo tc qdisc change dev eth1 root netem loss 0% corrupt 0.2% duplicate 0% delay 3 reorder 0% 0%
## dest
sudo tc qdisc change dev eth2 root netem loss 0% corrupt 0.2% duplicate 0% delay 3 reorder 0% 0%

#reordering
## broker
sudo tc qdisc change dev eth3 root netem loss 0% corrupt 0% duplicate 0% delay 3 reorder 1% 50%
## r1
sudo tc qdisc change dev eth1 root netem loss 0% corrupt 0% duplicate 0% delay 3 reorder 1% 50%
## dest
sudo tc qdisc change dev eth2 root netem loss 0% corrupt 0% duplicate 0% delay 3 reorder 1% 50%

 
