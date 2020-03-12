# SwitchHosts!

# hm49
127.0.0.1	localhost
255.255.255.255	broadcasthost
::1             localhost
0.0.0.0 https://account.jetbrains.com:443
127.0.0.1 manage.leyou.com
127.0.0.1 api.leyou.com
47.104.131.83 image.leyou.com



	server {
        	listen       80;
        	server_name  api.leyou.com;

		location /api/upload {
		   proxy_pass http://127.0.0.1:8082;
		   rewrite "^/api/(.*)$" /$1 break;
		}

	        location / {
        	   proxy_pass http://127.0.0.1:10010;
        	}
	}
	server {
		listen	     80;
		server_name  image.leyou.com;
		
		location /{
		   root /Users/dayongsun/IdeaProjects/heima/image;
		}
	}
