# clj-wiremock

[![Build Status](https://travis-ci.org/alexanderjamesking/clj-wiremock.svg)](https://travis-ci.org/alexanderjamesking/clj-wiremock) 

A Clojure library that wraps [wiremock](https://github.com/tomakehurst/wiremock) by [@superaking](https://twitter.com/superaking)

[![Clojars Project](http://clojars.org/clj-wiremock/latest-version.svg)](http://clojars.org/clj-wiremock)

### Hello World in the REPL

#### Prerequisites
You have an up to date version of [leiningen](https://github.com/technomancy/leiningen)
You have cloned this git repo and run ```lein repl``` to start the REPL

```clojure
(require '[clj-wiremock.core :refer :all])

; create a new server on the default port 8080
(def wiremock-server (server))

; or to use a custom port pass a config to the server
(def wiremock-server (server (config { :port 11111 })))

; start the server - load http://localhost:8080/__admin/ in a browser to see it running
(start wiremock-server)

; set up a stub then refresh the __admin page to see your new mapping
(stub { :request { :method "GET" :url "/hello"} 
        :response { :status 200 :body "Hello World"}})

; load http://localhost:8080/hello in a browser

; reset the mappings - handy when you want to clear state between tests
(reset wiremock-server)

; stop the server
(stop wiremock-server)
```

###A practical example

See [alexanderjamesking/clj-wiremock-example](https://github.com/alexanderjamesking/clj-wiremock-example) for an example of using wiremock to test a webapp that makes a HTTP call to a stubbed server that returns JSON.

