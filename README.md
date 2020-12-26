# A2k-url-shortener

It's a simple URL shortener for NodeJS.

As it's designed for private use, considering the links number won't be very large, A2k uses **TEXT FILE** instead of a database to store links. And it will read all links data to memory when starts.

Demo https://www.a2k.xyz

![biu screenshot](/images/screenshot.png?raw=true)

**Hint**  
Click "shorten it" with meta/ctrl key to ignore existing path and overwrite it.

## Configuration

config.json (the values below are defaults)

```javascript
{
    // the text file that saves links data
    "linksFile": "links.txt",

    // a regex (string form) that tests whether the url is valid
    "urlRegex": "^\\w+:\\S+$",
    
    // a regex (string form) that tests whether the shortened path is valid
    "pathRegex": ".",
    
    // the entrance of this biu
    // change it to something else if you want to use this biu privately
    "entrance": "/",

    // redirect url for path not matching any existing records
    // the path (without leading /) will be added to the value directly
    "redirect": null,
    
    // port to listen, fallbacks to process.env.PORT or 1337
    "port": 1337
}
```

## API

The API URL is the same as the entrance.

E.g. as https://www.a2k.xyz has it entrance set to "/", the API URL is https://www.a2k.xyz/; Or if its entrance is "/xxx", the API is then https://www.a2k.xyz.

### Method and Formats

Use POST method to invoke the API. Accepted Content-Type includes urlencoded (application/x-www-form-urlencoded) and JSON (application/json). The response is always in JSON.

### Request Parameters

**type** should always be string "add".  
**url** the url to be shortened.  
**path** (optional) custom path.  
**force** (optional) if path is specified, true to ignore and overwrite if it already exists.  

### Response

#### Success

```typescript
{
    path: string
}
```

Here path is not full url, append it to the base url to make it complete.

#### Error

```typescript
{
    error: {
        message: string,
        code: number
    }
}
```
