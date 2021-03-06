
Udp helper
==========

This helper allows to start an UDP server listenig on a specific port
and send UDP packets to a remote host.

Let's start with an example. We want to add a server listening on port
7777.

First of all create a new helper and start the server specifying ip
address, port number and a listener

.. code:: java

      UdpHelper udpserver = new UpdHelper();
      udpServer.startServer("0.0.0.0", 7777, new UdpListener() {
                @Override
                public void onDataAvailable(String sourceAddress, Integer sourcePort, String data) {
                    System.out.println("UDP packet received: {0}", data);
                    // here add the code to execute when a packet is received
                });

When a new packet arrives you can see the payload on the log as a string
and execute any code added to **onDataAvailable** method.

It'd be better to stop the server and unbound the port with

.. code:: java

       udpServer.stop()

How to send a packet
--------------------

To send a packet you need only the ip and port number of the remote host
and a string representing the payload.

For example:

.. code:: java

    udpServer.send("192.168.0.120", 8899, "payload to send");
