# Encode and Decode Tiny URL
Draft Java solution (random fixed-length encoding approach):
```
    String alphabet = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
    HashMap<String, String> map = new HashMap();
    Ranfom rand = new Random();
    String key = getRand();

    public String getRand(){
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < 6; ++ i){
            sb.append(alphabet.charAt(rand.nextInt(62)));
        }
        return sb.toString();
    }

    // Encodes a URL to a shortened URL.
    public String encode(String longUrl) {
        while(map.containsKey(key)){
            key = getRand();    //in case of collision
        }
        map.put(key, longUrl);
        return "http://tinyurl.com/" + key;
    }

    // Decodes a shortened URL to its original URL.
    public String decode(String shortUrl) {
        return map.get(shortUrl.replace("http://tinyurl.com/", ""));
    }
```