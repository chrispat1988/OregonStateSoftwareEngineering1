
# Software Engineering 1-Microservices
# ZeroMQ

ZeroMQ (also known as ØMQ, 0MQ, or zmq) looks like an embeddable networking library but acts like a concurrency framework. It gives you sockets that carry atomic messages across various transports like in-process, inter-process, TCP, and multicast. You can connect sockets N-to-N with patterns like fan-out, pub-sub, task distribution, and request-reply. It's fast enough to be the fabric for clustered products. Its asynchronous I/O model gives you scalable multicore applications, built as asynchronous message-processing tasks. It has a score of language APIs and runs on most operating systems.

# How to Install

Pyzmq
Github	https://github.com/zeromq/pyzmq
Docs	https://pyzmq.readthedocs.io/en/latest/
Guide	http://zguide.zeromq.org/py:all
pypi	https://pypi.org/project/pyzmq/
Download

pip install pyzmq

# How to Request and Receive Data

The user will be able to request data by requesting the time that they want to input by entering the hour, minute and second that they want the timer to start on the client server side. Once that request is made from the client side, the server will receive that request, and then proceed to reply with the request.

Example

context = zmq.Context()
socket = context.socket(zmq.REP)
socket.bind("tcp://127.0.0.1:8888")

Though I used a IP address for my implementation, you can also utilize localhost as well.

while True:

    message_prompt1=input("Enter your time in hours.")
    message_prompt2=input("Enter your time in minutes.")
    message_prompt3=input("Enter your time in seconds.")
    socket.send_string(message_prompt1)
    socket.send_string(message_prompt2)
    socket.send_string(message_prompt3)

Once this happens, the server then sends back the request to the user.

    message_prompt1 = socket.recv()
    message_prompt2 = socket.recv()
    message_prompt3 = socket.recv()
    print('From client:', message_prompt1)
    print('From client:', message_prompt2)
    print('From client:', message_prompt3)

And thus the timer will then activate for the client to use.


# UML Sequence Diagram

![Chris Patton Sequence Diagram](https://user-images.githubusercontent.com/86307096/218897215-1ea364cb-b0c5-4d11-8749-be2e24d393de.jpg)
