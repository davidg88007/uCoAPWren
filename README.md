## uCoAPWren

This is exploratory code referenced in one [blog post]() of a series, exploring the use of [Wren](https://github.com/wren-lang/wren) on microcontrollers.
This version of the CoAP server code has only been tested on Ubuntu, exercised via the [libcoap](https://github.com/obgm/libcoap) command line tool
 coap-client.

 
[microcoap](https://github.com/1248/microcoap) is used as an interface to the Wren VM, exposing 2 endpoints:
- coap://\<server\>/wren/about
- coap://\<server\>/wren/try

You can try the following commands from the client:

- `coap-client -v 100 -m get coap://127.0.0.1/wren/about`
- `coap-client -e "var e = [1, 3]\ne.insert(1, 4)\nSystem.print(e)\n" -m post coap://127.0.0.1/wren/try`

For simplicity, wrenAll.c was used to expose the Wren VM, as generated by
`python3 generate_amalgamation.py` in the Wren util directory.

The only modification to the original microcoap code, was to implement
the two request handlers, in the file `endpoints.c`
