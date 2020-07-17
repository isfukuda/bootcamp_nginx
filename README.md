# bootcamp_nginx
## はじめに
- VMに下記のツールを準備（package manager経由でインストール）してください
  - git
  - openssl
  - docker
 
## 使い方
- 手元のVM環境へ git clone
  ```
  # git clone https://gh.iiji.jp/s-fukuda/bootcamp_nginx.git
  ```
- 最初に nginx のdockerfileを使って docker run 実行
  ```
  # cd nginx
  # docker build -t docker-nginx .
  # docker run --rm --name nginx -d -p 80:80 -p 443:443 docker-nginx:latest
  
  # docker ps -a
  CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS              PORTS                                     NAMES
  f50d30edc442        docker-nginx:latest   "nginx -g 'daemon ..."   15 hours ago        Up 15 hours         0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp   nginx
  ```
- 次に nginx_inc フォルダを使って同じ様に docker run 実行
  ```
  # docker build -t docker-nginx .
  # docker run --rm --name nginx -d -p 80:80 -p 443:443 docker-nginx:latest
  ```
- VMから openssl コマンドを使って 3. の実行環境へTLS接続を試す
  ```
  # openssl s_client -connect 0.0.0.0:443 -servername localhost
  ```
- VMから curl コマンドを使って自作環境の詳細な応答を得る
  ```
  $ curl -o /dev/null https://0.0.0.0:443 -w @format.txt -s -k
  ```
- on the fly 
  [http://nginx.org/en/docs/control.html]
