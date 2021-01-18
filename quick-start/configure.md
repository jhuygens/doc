# Configure

## API configuration

The default configuration file of Huygens Search Api is: `./config.json`

{% hint style="info" %}
The default configuration is sufficient for the basic operation of the API.
{% endhint %}

### General configurations

Change encryption keys and cache timeouts

{% code title="config.json " %}
```javascript
...
    "general": {
        "app_version": "1.0.7",
        "session_life_time": "1h",
        "secure_secret_key": "75ABC8764512FADBCE234765623DFA45",
        "secure_secret_iv": "5422AFECBCBCB675",
        "secure_token_key": "75ABC8764512FADBCE234765623DFA47",
        "secure_token_iv": "5422AFECBCBCB675",
        "default_secret_expire": 3600,
        "default_token_expire": 3600,
        "default_cache_expire": 3600,
        "password_secure_cost": 10,
        "host": "http://localhost:9092",
        "port": 9001
    },
    ...
```
{% endcode %}

### Services configuration:

{% code title="config.json" %}
```javascript
...
   "services": {
        "auth": {
            "port": 9091
        },
        "search": {
            "port": 9092,
            "paging": {
                "search": {
                    "url": "http://localhost:9092/v1/search" // Configure de host in url pagin objects response 
                }
            }
        },
        "logger": {
            "port": 9021,
            "events": {
                "path": "./logger/events"
            },
            "logs": {
                "path": "./logger/logs"
            }
        }
    },
...
```
{% endcode %}

### Configure a new searcher

{% hint style="warning" %}
Implement the [searcher-engine](https://github.com/jhuygens/searcher-engine) package and import in `main.go` file from [search-service](https://github.com/jhuygens/search-service) repository. [Compile](https://docs.docker.com/engine/reference/commandline/build/) a new image of this module.
{% endhint %}

{% code title="search-service/main.go" %}
```go
package main 

import (
	"bytes"
	"encoding/json"
	"fmt"
	"io/ioutil"
	"net/http"

	"github.com/gorilla/mux"
	"github.com/jgolang/api"
	"github.com/jgolang/config"
	"github.com/jgolang/log"
	"github.com/jgolang/redis"
	"github.com/jhuygens/cache"
	"github.com/jhuygens/security"

	// search-engine autoregistry searchers
	_ "github.com/jhuygens/crcind-searcher"
	_ "github.com/jhuygens/itunes-searcher"
	_ "github.com/jhuygens/tvmaze-searcher"
	// Your searcher-engine package implementation
	_ "github.com/firulais/my-implement-searcher"
)

...
```
{% endcode %}

Add your implement configuration to config.json file:

{% code title="config.json" %}
```go
// Add the searcher custom name
...
    "searchers": {
        "itunes": "itunes",
        "tvmaze": "tvmaze",
        "crcind": "crcind"
        "firulais": "myfiru"
    },
...
// Add the integration service provider
    "integrations": {
        "firulais": {
            "endpoint": "https://api.firulais.com/search",
            "timeout": 20
        },
        "itunes": {
            "endpoint": "https://itunes.apple.com/search",
            "timeout": 20
        },
        "tvmaze": {
            "endpoint": "http://api.tvmaze.com/search/shows",
            "timeout": 20
        },
        "crcind": {
            "endpoint": "http://www.crcind.com/csp/samples/SOAP.Demo.CLS",
            "action": "GetByNameResponse",
            "timeout": 20
        },
        "logger": {
            "events": {
                "endpoint": "http://localhost:9021/logger/events",
                "timeout": 20
            },
            "logs": {
                "endpoint": "http://localhost:9021/logger/logs",
                "timeout": 20
            }
        }
    }
...
```
{% endcode %}

