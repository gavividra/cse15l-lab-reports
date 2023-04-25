Part 1:
- 
Write a web server called StringServer that supports the path and behavior described below. It should keep track of a single string that gets added to by incoming requests. The requests should look like this: `/add-message?s=<string>`

My code for StringServer.java:
````
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String result = "";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                result += parameters[1] + "\n";
                return result;
            }
        }
        return "404 Not Found!";
    }
}

public class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
````

![](FirstLine.png)

The handleRequest and main method are both called when making this server that adds strings. 
The main method runs after `java StringServer 4000` is called as it checks to make sure the port number 4000 is within range and available. If so, it then creates a new server using this port number with the line of code `Server.start(port, new Handler())`.
The handleRequest method runs to make sure the line `/add-message?s=` is called after the server. After detecting this line is called, it then returns the following as a string. This can be seen on the server in the picture above.



![](SecondLine.png)

In this second picture, another message is saved, and it is added to the initial messages. This is because the values are saved to the String result and are seperated by a next line function (`\n`): `result += parameters[1] + "\n"`


Part 2:
- 

Part 3:
- 


