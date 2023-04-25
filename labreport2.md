Part 1:
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

![](firstline.png)
Which methods in your code are called?
- 
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
- 
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
- 

![](secondline.png)
Which methods in your code are called?
- 
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
- 
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
- 


Part 2:

Part 3:

