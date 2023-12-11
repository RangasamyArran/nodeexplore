# NODE -  Notes
// create server
var http = require('http');'
 
var server = http.createServer(
              function(req, resp){
 } );
 
 server.listen(any port);
 

 //send respone
 //set header
 resp.writeHead(responecode, {headername:"header value"});
 //set body
 resp.write("content of the body");

 //post request:
    In Node fetch data through event handling which is taken care of built in class event Emitter
   


## Routing in Node
    - Mapping different url pattern with different functionality

## Event 
    * Event Emitter class has two events 
        data - post request come to the server
        end - Data fetching is done
    * in Event Emitter has two method 
        on -> bind an event(data or end) to any object
           -> 'on' takes two parameter (event and callback function)

        emit - Trigger an event
            - it takes one param event name
    * Custom event
        - To create custom event,

        -  first load event module
             var events = require('events')
        - Create a constructor function 
             var class_name = function(){}
        - inherit the constructor function from event emitter class
             util.inherits(class_name, EventEmitter);
        - Extend the prototype of the constructor function and add a method which can emit the custom event
             ````js
             class_name.prototype.method_name = function(){
                class_obj.emit(eventname);
                }
                ```
        - Listen the event and perform appropriate action
        * class_obj.on(eventname, function(){});

## NPM - Node Package Manager
    - Official package manager for Node
    - Provide two functionality
        - online respository
        - command line utility
## File System:
    - Built in module 'fs'
    fs has synchronus and asynchronus function




## Stream 
        - Simplifies input / output operations
       - read data from a source and bind it to a destination
       - It is an event Emitter and implements some special methods.


    Readable Stream - allow stream(createStream) read the data from source
    - methods:                      Events
        - read();                   data/readable
        - setEncoding(encoding)     end
        - resume()                  close
        - puase()                   error
        - pipe()

    Writable Stream - allow stream to write to destination
    - methods                       Events
        - write();                  drain
        - setEncoding(encoding)     finish
        - end()                     pipe
                                    error
    piping stream - Taking input from one stream and passing into another stream without putting into buffer, we can avoid event handing code 
                    sourceread.pipe.destinationstream
    Transformstream - Tranform stream from source and put into destination w[ith change
        - two APIs 
            Zlib - compression/decompression
            Crypto - encryption/decryption
## NetModule
    -  Netmodule helps to Write a scoket programming in node,  
    -  there are two kind of scoket programming
        TCP server - Listen for connection
        TCP client - sends request to servers
    - Net - module is an async wrapper
    - TCP server callback has two events
        data -  when ever clients sends a data event will be triggered         
        close - once server is disconnected, close will be triggered ie client would have triggered a function client.end();
        ``` js
                var server = net.createServer(function(conn){
            console.log("Client connected");
            conn.on('data', function(data){
                console.log("data sent by client -> "+data);

            });

            conn.on('close', function(){
                console.log("Connecttion closed by client");
            });
            //send call back response to client
            conn.write('Hello Client, Hope you enjoyed the service');

        });
    ```
    - TCP Client
        client uses 'connect' function
        when client receives any response then data event will be triggered
        client.end  function will disconnect from server
        when client disconnected 'end' event will be triggered

  
## REST in Node
    - restler is the module helps create REST service in node
    ```js
    npm install restler
    ```
## How to scale node application
    * node alway run single thread
    * child_process module
        - it felicitate child_process
        - there are three ways to create child child_process
            - exec()
                this method launches new child process and runs the command in shell
                ```
                    exec(command, [option], callback);
                ```
            - spawn()
                this launches new child process and return a child process object
                ```
                    spawn(command, [args], [options] )
                ```
            - fork()
                specilized method of spawn()
                ```
                    fork(modulepath, [args], [options])
                ```
    * Cluster module
        Cluster module is built on top of child_process.fork() method which is used to do the load balancing between the child process running in parallel


