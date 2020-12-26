# A2k-url-shortener

It's a simple URL shortener for NodeJS.

As it's designed for private use, considering the links number won't be very large, A2k uses **TEXT FILE** instead of a database to store links. And it will read all links data to memory when starts.

Demo https://www.a2k.xyz

![a2k screenshot](https://cdn.discordapp.com/attachments/792298559634538529/792510296286822400/unknown.png)

**Hint**  
Click "shorten it" with meta/ctrl key to ignore existing path and overwrite it.


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
