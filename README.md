# libTCP

It's a naive and easy use library.

This library contains server and client implementations.

## Dependency
This library only can run in the **Linux**.

## Contents

|sample name|description|
|-----------|-----------|
|libTCP.hpp |The library|
|s.cpp      |A sample program of server|
|c.cpp      |A sample program of client|


## Usage

### Server program
```
#include <iostream>
#include "libTCP.hpp"

int main()
{
	TCP::Server server(50030);
	
	while(true){
		for (int i = 0; i < 100; i++) {
			std::string msgs = server.receive();
			std::cout << msgs << std::endl;
			msgs += "!";
			server.send(msgs);
		}
		server.reinitialize(50030);
	}

	
	return 0;
}
```

### Client program
```
#include <iostream>
#include "libTCP.hpp"

int main()
{
	TCP::Client client(50030);

	for (int i = 0; i < 100; i++) {
		std::string msgs("hello");
		std::cout << "[Send]\t" << msgs << std::endl;
		client.send(msgs);
		std::cout << client.receive() << std::endl;
	}
	
	return 0;
}
```

