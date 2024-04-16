# This is Lab Report 2 - Servers and SSH Keys (Week 3)

## Part 1 - ChatServer
Code: <br/>
```
import java.io.IOException;
import java.net.URI;
import java.net.URISyntaxException;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String messageHistory = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return messageHistory;
        }
        else if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("&");
            messageHistory = messageHistory + parameters[1].substring(parameters[1].indexOf("=") + 1) + ": " + parameters[0].substring(parameters[0].indexOf("=") + 1) + "\n";
            return messageHistory;
        }
        return messageHistory;
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

class URIMain {
  public static void main(String[] args) throws URISyntaxException {
    URI uri = new URI("http://ieng6-202.ucsd.edu:4000/");
    System.out.println(uri.getHost());
    System.out.println(uri.getPath());
    URI anotherURI = new URI("http://ieng6-203.ucsd.edu:4000/search?q=hello");
    System.out.println(anotherURI.getHost());
    System.out.println(anotherURI.getPath());
    System.out.println(anotherURI.getQuery());
  }
}
```
Screenshots: <br/>
