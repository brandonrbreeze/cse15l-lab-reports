# Part 1

    import java.io.IOException;

    import java.net.URI;

    import java.util.*;

    class Handler implements URLHandler {
        // The one bit of state on the server: a number that will be manipulated by
        // various requests.
        Vector<String> stringVector = new Vector<>();

        public String handleRequest(URI url) {
            if (url.getPath().equals("/")) {
                return "Welcome\n";
            }else {
                System.out.println("Path: " + url.getPath());
                if (url.getPath().contains("/add")) {
                    String[] parameters = url.getQuery().split("=");
                    if (parameters[0].equals("s")) {
                        stringVector.add(parameters[1]);
                    }
                    return "added";
                }
                else if(url.getPath().contains("/search")){
                    Vector<String> newStringVector = new Vector<>();
                    String[] parameters = url.getQuery().split("=");
                    if (parameters[0].equals("s")) {
                        String search = parameters[1];
                        for(String x : stringVector){
                            if(x.contains(search)){
                                newStringVector.add(x);
                            }
                        }
                        return newStringVector.toString();
                    }
                }
                return "404 Not Found!";
            }
        }
    }

    public class SearchEngine {
        public static void main(String[] args) throws IOException {
            if(args.length == 0){
                System.out.println("Missing port number! Try any number between 1024 to 49151");
                return;
            }

            int port = Integer.parseInt(args[0]);

            Server.start(port, new Handler());
        }
    }

    
    // A simple web server using Java's built-in HttpServer

    // Examples from https://dzone.com/articles/simple-http-server-in-java were useful references

    import java.io.IOException;
    import java.io.OutputStream;
    import java.net.InetSocketAddress;
    import java.net.URI;

    import com.sun.net.httpserver.HttpExchange;
    import com.sun.net.httpserver.HttpHandler;
    import com.sun.net.httpserver.HttpServer;

    interface URLHandler {
        String handleRequest(URI url);
    }

    class ServerHttpHandler implements HttpHandler {
        URLHandler handler;
        ServerHttpHandler(URLHandler handler) {
            this.handler = handler;
        }
        public void handle(final HttpExchange exchange) throws IOException {
            // form return body after being handled by program
            try {
                String ret = handler.handleRequest(exchange.getRequestURI());
                // form the return string and write it on the browser
                exchange.sendResponseHeaders(200, ret.getBytes().length);
                OutputStream os = exchange.getResponseBody();
                os.write(ret.getBytes());
                os.close();
            } catch(Exception e) {
                String response = e.toString();
                exchange.sendResponseHeaders(500, response.getBytes().length);
                OutputStream os = exchange.getResponseBody();
                os.write(response.getBytes());
                os.close();
            }
        }
    }

    public class Server {
        public static void start(int port, URLHandler handler) throws IOException {
            HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);

            //create request entrypoint
            server.createContext("/", new ServerHttpHandler(handler));

            //start the server
            server.start();
            System.out.println("Server Started! Visit http://localhost:" + port + " to visit.");
        }
    }

![Image](/SearchMain.png)

**This is the main page for the search engine**

* When the program is ran from the terminal we give it a unique port number.
* Main takes that number and puts it into Server class method called start.
* Start takes an interger for the port number and a URLHandler class object
* Start creates a local server address by calling a method from class HttpServer called createContext. I'm gonna be honest, all I understand about createContext is that is creates a request entry point.
* Once the server is started we can access it through a local browser as shown in the image
* When it is accessed, handleRequest of class Handler is called
* The Handler only contains one field, a public String Vector object
* The input for handleRequest is the url object
* The URL object calls getPath to get the url path
* If the url path is just "/", then I set the handleRequest to return "Welcome" to the screen
* If the url path contains "/add" then handles takes the string input after "?s=" and puts it into the String Vector

![Image1](/SearchAdd.png)

* If the url path contains "/add" then handRequest takes the string input after "?s=" and puts it into the String Vector and outputs "added" to the screen

![Image2](/SearchSearch.png)

* If the url path contains "/search" then handRequest takes the string input after "?s=" and searchs the String Vector for all of the strings containing the input and outputs them to the screen

# Part 2

## File: ListExamples.java

### Method: filter

**Failure Inducing Input**

    public class ListTests {
        @Test 
        public void testFilter() {
            List<String> test = new ArrayList<>();
            StringCheck check = new StringCheck();
            test.add("hello");
            test.add("");
            test.add("bits");
            List<String> expectedTest = new ArrayList<>();
            expectedTest.add("hello");
            expectedTest.add("bits");
            assertEquals(expectedTest.toString() , ListExamples.filter(test, check).toString());
        }
    }

* I made a class that implements the string checker interface. checkString returns true if a string is not empty
* We expect the output to be a new string list without the empty string and in the same order

**The Symptom**

![Image3](/Listtestfail.png)

* The actual output is not in the same order

**The Bug**

~~~~
    static List<String> filter(List<String> list, StringChecker sc) {
        List<String> result = new ArrayList<>();
        for(String s: list) {
            if(sc.checkString(s)) {
            result.add(s);
            }
        }
        return result;
    }
~~~~

* result.add( 0, s ) constructed the new list in reverse. The fix was result.add(s);

**The Connection**

* The symptom was that the list was reversed
* The bug caused the symptom by adding to the list in reverse
* The bug caused the symptom with any input size larger than 1

## File: ArrayExamples.java

### Method: Reversed 

**Failure Inducing Input**

~~~~
@Test
public void testReversed2() {
    int[] input1 = { 1, 2 };
    assertArrayEquals(new int[]{ 2, 1 }, ArrayExamples.reversed(input1));
}
~~~~

* We Expect the output to be in reverse order

**The Symptom**

![Image3](/arrayTestsymp.png)

* The symptom was that is reverse returned an array of elements of 0

**The Bug**


~~~~
 static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[arr.length - i - 1] = arr[i];
    }
    return newArray;
  }
~~~~

* The bug was that the new list was not having any values assigned to it 

~~~~
arr[i] = newArray[arr.length - i - 1];
~~~~

* It should have been

~~~~
newArray[arr.length - i - 1] = arr[i];
~~~~

**The Connection**

* The symptom was that the new array was essentailly emtpy
* The bug was that no element were being put into the new list
* The bug caused the symptom when given any input in which the elements in the array are non-zero