## License

Copyright 2011 Daniel Arndt

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

Author: 
    Daniel Arndt <danielarndt@gmail.com> (http://dan.arndt.ca)

## Purpose

The purpose of this program is to calculate flow statistics from a given 
capture file. Flowtbag was designed with offline processing as the primary
focus.

## Requirements

To run the executable, you will need libpcap installed. On a debian based
system, the following command will install the appropriate library:

    apt-get install libpcap

Other distributions will likely have a similar package name.

To compile from source, you'll need a Go compiler, libpcap headers, and
gopcap.

### Go compiler:

Please see http://golang.org/doc/install.html

### libpcap headers:

On a debian based system, you can execute the following command:

    apt-get install libpcap-dev

Other distributions will likely have a similar package name. It is
important that if you are compiling the program from source, you install
the developement headers.

## Compilation

Once libpcap is installed, `go` will install the necessary go dependencies. Just
build and install using go.

   go get github.com/danielarndt/flowtbag

## Usage

The program's usage is currently left undocumented due to the rapidly
changing functionality of the program in its early stages. However, if you
run flowtbag, the currently implemented options should be displayed. A
typical use case might look something like:

    $ ./flowtbag test.cap > test.out

## Output

Flowtbag currently has two seperate channels for output. To stdout, a stream
of comma seperated values is output. Line by line, these represent the flows
in the capture. The features output are given, in order, in section 4.1. The
second output channel is stderr. This is where reports, as well as any
debugging information is displayed. This allows the user to redirect output
to a text file, and still receive updates as the program runs. The setup for
output is likely to change in future versions of Flowtbag when a better
system is designed.

### Features
srcip - (string) The source ip address 
srcport - The source port number 
dstip - (string) The destination ip address 
dstport - The destination port number 
total_fpackets - Total packets in the forward direction 
total_fvolume - Total bytes in the forward direction 
total_bpackets - Total packets in the backward direction 
total_bvolume - Total bytes in the backward direction 
min_fpktl - The size of the smallest packet sent in the forward direction (in bytes) 
mean_fpktl - The mean size of packets sent in the forward direction (in bytes) 
max_fpktl - The size of the largest packet sent in the forward direction (in bytes) 
std_fpktl - The standard deviation from the mean of the packets sent in the forward direction (in bytes) 
min_bpktl - The size of the smallest packet sent in the backward direction (in bytes) 
mean_bpktl - The mean size of packets sent in the backward direction (in bytes) 
max_bpktl - The size of the largest packet sent in the backward direction (in bytes) 
std_bpktl - The standard deviation from the mean of the packets sent in the backward direction (in bytes) 
min_fiat - The minimum amount of time between two packets sent in the forward direction (in microseconds) 
mean_fiat - The mean amount of time between two packets sent in the forward direction (in microseconds) 
max_fiat - The maximum amount of time between two packets sent in the forward direction (in microseconds) 
std_fiat - The standard deviation from the mean amount of time between two packets sent in the forward direction (in microseconds) 
min_biat - The minimum amount of time between two packets sent in the backward direction (in microseconds) 
mean_biat - The mean amount of time between two packets sent in the backward direction (in microseconds) 
max_biat - The maximum amount of time between two packets sent in the backward direction (in microseconds) 
std_biat - The standard deviation from the mean amount of time between two packets sent in the backward direction (in microseconds) 
duration - The duration of the flow (in microseconds) 
min_active - The minimum amount of time that the flow was active before going idle (in microseconds) 
mean_active - The mean amount of time that the flow was active before going idle (in microseconds) 
max_active - The maximum amount of time that the flow was active before going idle (in microseconds) 
std_active - The standard deviation from the mean amount of time that the flow was active before going idle (in microseconds) 
min_idle - The minimum time a flow was idle before becoming active (in microseconds) 
mean_idle - The mean time a flow was idle before becoming active (in microseconds) 
max_idle - The maximum time a flow was idle before becoming active (in microseconds) 
std_idle - The standard devation from the mean time a flow was idle before becoming active (in microseconds) 
fpsp - The percentage of small packets in the flows (foward)
bpsp - The percentage of small packets in the flows (backward)
fpmp - The percentage of medium packets in the flows (foward)
bpmp - The percentage of medium packets in the flows (backward)
fplp - The percentage of largest packets in the flows (foward)
bplp - The percentage of largest packets in the flows (backward)
