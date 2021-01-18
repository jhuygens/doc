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
Implement this package and registry in main.go from search-service repository. [Compile](https://docs.docker.com/engine/reference/commandline/build/) a new image of this module.
{% endhint %}

