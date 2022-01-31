# Challenge description

Let's warmup a little bit now with some cool stuffs! Web is really always the best!!

Link: http://20.119.58.135:4567/leetstatus

**Author: Kahla**

-----------------------------------------------------------

![c](https://user-images.githubusercontent.com/58823465/151862530-52d045f4-912a-4ade-8e36-c3651dfd416e.png)


At first i didn't know where to go and how to try to solve this 
i tried to check for robots.txt or index.php or index.html .. couldn't find anything until i checked the source code that was provided 

it seems like the website is running using nginx ! 


looking into `main.py` we see this :

```python
from flask import Flask
import os

flag=os.getenv("FLAG")
app = Flask(__name__, static_url_path='/static/')
@app.route("/v1/status")
def index():
	return "Everything is good afaik"

@app.route("/flag")
def flag():
	return flag

if __name__ == '__main__':
	app.run()
```
nginx config file :

```
server {
listen 80;
server_name welcome.task;

location /leet {
  proxy_pass http://api:5000/v1/;
}

access_log off;
error_log /var/log/nginx/error.log error;
}
```

From this we can conclude that the `"leet"` part is like a prefix for the other webpages 
After few googling i figured that we can try to find the path to /flag 
===> path traversal !! 

and this is possible because of the misconfiguration of nginx 

you can read more about this here : 

https://www.acunetix.com/vulnerabilities/web/path-traversal-via-misconfigured-nginx-alias/

finally we find the path to be ../flag

Path : `http://x.x.x.x/leet../flag`


and we get our flag :

`Securinets{Nginx_Is_NoT_ThaT_GooD_AftER_All}`



