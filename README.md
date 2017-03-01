# UE 2017

### Basic Nginx Configuration
Inside `location / { } ` block just replace it to: `try_files $uri $uri/ /index.php?$query_string;` should look like this:

```nginx
...
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

...
```
