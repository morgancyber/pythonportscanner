Introduction

Hey! Welcome to my Python port scanner tutorial.A port scanner is a tool that scans a range of network ports on a target system to determine which ports are open or closed. This information can be used to identify potential security vulnerabilities or to test the functionality of network services. In this tutorial, we will build a simple port scanner using Python.
Prerequisites

Before we begin, make sure you have Python 3 installed on your system. You will also need to have basic knowledge of networking concepts and the socket module in Python.
Setting up the Target Host and Port Range

The first thing we need to do is set up the target host and port range that we want to scan. We can prompt the user to enter the target host and the list of ports to scan using the input() function:


target_host = input("Enter the target host: ")
target_ports = input("Enter the target ports (comma separated): ")

We can convert the comma-separated list of ports to a Python list of integers using the split() and int() functions:


target_ports = [int(port) for port in target_ports.split(",")]

Scanning the Ports

Now that we have our target host and port range set up, we can start scanning the ports. We can use a for loop to iterate through each port in the range and attempt a connection using the socket module.


import socket

for port in target_ports:
    # create a socket object
    client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # set a timeout for the connection attempt
    client.settimeout(1)
    try:
        # attempt to connect to the target host/port
        client.connect((target_host, port))
        # if the connection succeeds, print the port is open
        print(f"Port {port} is open")
    except:
        # if the connection fails, print the port is closed
        print(f"Port {port} is closed")
    # close the socket
    client.close()

Inside the for loop, we create a new socket object and set a timeout of 1 second for the connection attempt using the settimeout() method. We then try to connect to the target host and port using the connect() method. If the connection is successful, we print a message indicating that the port is open. If the connection fails, we print a message indicating that the port is closed. Finally, we close the socket using the close() method.
Testing the Port Scanner

Now that we have our port scanner script ready, let's test it out. Save the script to a file named portscanner.py and run it from the command line:

python portscanner.py

You will be prompted to enter the target host and the list of ports to scan. Enter the information and press Enter. The script will scan the target ports and print a message indicating whether each port is open or closed.
Conclusion

In this tutorial, we built a simple port scanner using Python. This port scanner is a basic implementation and may not work for all scenarios. It also has the potential to generate a lot of network traffic, so use caution when scanning large numbers of ports or targets. Additionally, port scanning can be used for malicious purposes, so make sure you have permission before scanning any network or system.
