---
layout: default
title: java-httpserver. The best named library ever!
---

`java-httpserver` is a relatively simple HTTP server plugin for Java.
It also has the most original and best name ever.

To get and start using `java-httpserver`, check out our GitHub project page, [https://github.com/dkuntz2/java-httpserver](https://github.com/dkuntz2/java-httpserver).

## Using java-httpserver is easy!

{% highlight java linenos %}
import httpserver.*;

public class myHandler extends HTTPHandler {
    public static void main(String[] args) {
        try {
            HTTPServer s = new HTTPServer();
            HTTPRouter r = new HTTPRouter();
            r.addHandler("*", new myHandler());

            s.setRouter(r);
            s.run();
        } catch (HTTPException e) {
            System.out.println("Server encountered an exception...");
            e.printStackTrace();
        }
    }

    public myHandler() throws HTTPException {
        addGET("/", "index");
    }

    public void index(HTTPResponse resp) {
        resp.setBody("Hello World!");
    }
}
{% endhighlight %}

Okay, so there are probably some frameworks that look easier and don't have the same amount of boilerplate we do. That said, when you get down to the actual handling content (lines 18 to 24), it's fairly small and consise. Plus lines 4 through 16 are only needed once, and not in every handler.


## Why is this different from $x?

It probably isn't all that different from `$x`, which is partially the point. While `java-httpserver`'s original purpose was to [Storyteller](http://storytellersoftware.com) a nice HTTP server, we expanded the scope to make a nice framework that anybody could use with minimal fuss.

The biggest difference from most microframeworks is the separation of separate sub-routes into distinct `HTTPHandlers` instead of having one master router or routing table, or putting everything in main. The reason we chose to do this is that it helps keep methods that go together ... together. Java and REST are both noun-oriented, which made this separation logical to us.


## How did we get here?

`java-httpserver` came about from our work on [Storyteller](http://storytellersoftware.com). We needed a "real" HTTP server, and couldn't find any easy to integrate libraries with low dependencies and a relatively simple user interface.

`java-httpserver` takes inspiration from microframeworks like [Sinatra](http://sinatrarb.com), [Flask](http://flask.pocoo.org), and [Go](http://golang.org)'s built-in `net/http` library.

