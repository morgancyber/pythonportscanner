![image](https://user-images.githubusercontent.com/120361960/224517040-f90f5ac9-8481-43f4-9090-3daf80413bbd.png)


Hey guys! In this tutorial, we will be creating a simple Python port scanner script that will allow us to scan for open ports on a remote server. Port scanning is an important technique used by network administrators and security experts to detect potential vulnerabilities in their systems. We will be using the Python programming language to create a port scanner script that can be run from the command line.

Prerequisites:
Before we begin, you will need to have Python installed on your machine. You can download and install Python from the official website.

Step 1: Setting up the environment
First, open your preferred text editor and create a new file called "portscanner.py". Save it to a location of your choice.

Step 2: Importing necessary modules
Next, we need to import the necessary modules. Open the "portscanner.py" file and add the following lines of code at the top of the file:

![image](https://user-images.githubusercontent.com/120361960/224516952-d4be6d36-b680-4b46-9abf-d91883503436.png)


Step 3: Defining the port scanning function
We will now define a function that will perform the port scanning. This function will take in the IP address and port number(s) as parameters and will return a list of open ports.

Add the following lines of code after the import statements:

![image](https://user-images.githubusercontent.com/120361960/224516998-ef96f5bb-53d3-4847-8534-02d4823684fd.png)


Introduction:
In this tutorial, we will be creating a simple Python port scanner script that will allow us to scan for open ports on a remote server. Port scanning is an important technique used by network administrators and security experts to detect potential vulnerabilities in their systems. We will be using the Python programming language to create a port scanner script that can be run from the command line.

Prerequisites:
Before we begin, you will need to have Python installed on your machine. You can download and install Python from the official website.

Step 1: Setting up the environment
First, open your preferred text editor and create a new file called "portscanner.py". Save it to a location of your choice.

Step 2: Importing necessary modules
Next, we need to import the necessary modules. Open the "portscanner.py" file and add the following lines of code at the top of the file:

python

import socket

Step 3: Defining the port scanning function
We will now define a function that will perform the port scanning. This function will take in the IP address and port number(s) as parameters and will return a list of open ports.

Add the following lines of code after the import statements:

python

def scan_ports(target, ports):
    # Create a list to store the open ports
    open_ports = []

    # Split the port range (if specified) into start and end ports
    if "-" in ports:
        start_port, end_port = ports.split("-")
        start_port = int(start_port)
        end_port = int(end_port)
    else:
        start_port = end_port = int(ports)

    # Iterate over the range of ports and attempt a connection
    for port in range(start_port, end_port+1):
        # Create a new socket object
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)

        # Attempt to connect to the port
        result = sock.connect_ex((target, port))

        # If the connection was successful, add the port to the list of open ports
        if result == 0:
            open_ports.append(port)

        # Close the socket
        sock.close()

    # Return the list of open ports
    return open_ports

Step 4: Parsing the command-line arguments and calling the port scanning function
We will now parse the command-line arguments and call the port scanning function. Add the following lines of code to the end of the file:

![image](https://user-images.githubusercontent.com/120361960/224517001-e044a068-6748-4f00-96cf-46fb41cdffe7.png)


Step 5: Testing the script
Save the "portscanner.py" file and open a command prompt or terminal window. Navigate to the directory where the file is saved and enter the following command:

'python portscanner.py'

You will be prompted to enter the IP address of the target server and the range of ports to scan. Once you have entered the necessary information, the script will scan the specified ports and display the results.

Congratulations, you have created a simple Python port scanner script! You can now use this script to scan for open ports on any remote server. Please note that port scanning can be considered a security threat and should only be used for legitimate purposes.




