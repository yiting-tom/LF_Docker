# 目錄
[A. 簡介](#concept)
> [1. Docker 的誕生](#concept)  
> [2. Docker 的理念](#concept)  
> [3. Docker 的優勢](#concept)  
> [4. Docker 的組成](#concept)

[B. 常用指令](commands.md)  
> [1. images](#images)  
> [2. container](#container)  
> [3. others](#others)

# 常用指令
> ![commands](https://raw.githubusercontent.com/philipz/docker_practice/master/_images/cmd_logic.png)


## <span id='images'>1. images</span>

> ### :mag: 在[Docker Hub](https://hub.docker.com/)上搜尋images
> `$ docker search [OPTIONS] [image:tag]`
> > | OPTION | INFO |
> > | :-: | :-: |
> > | -s='星數' | 星星數量需大於多少 |
> > | --no-trunc | 列出完整訊息 |
> > | --automated | 只列出 automated build 的 image |
> 
> <br>
> 
> ### :arrow_down: 將images從[Docker Hub](https://hub.docker.com/)下載至本機
> `$ docker pull [image1:tag1] [image2:tag2][...]`  
> > | OPTION | INFO |
> > | :-: | :-: |
> > | -f | 使用[過濾器](https://docs.docker.com/engine/api/v1.40/#operation/ImageList) |
> 
> <br>  
> 
> ### :page_with_curl: 列出本機所有images
> `$ docker images [OPTIONS]`  
> > | OPTION | INFO |
> > | :-: | :-: |
> > | -q | 只列出 image id |
> > | -a | 列出中間層 images |
> > | --digests | 列出摘要訊息 |
> > | --no-trunc | 列出完整訊息 |
> 
> <br>
> 
> ### :wastebasket: 刪除本機images
> `$ docker rmi [image1:tag1] [image2:tag2] [...]`  
> > | OPTION | INFO |
> > | :-: | :-: |
> > | -f | 強制刪除 |
> > | --no-prune | 不刪除沒有tag的parent images |
> > 
> > :sparkles: `$ docker rmi $(docker images -qa)`
> 
> <br>

***

## <span id='container'>2. container</span>  

> ### :runner: 創建並啟動container
> `$ docker run [OPTIONS] [image:tag] [COMMAND] [args]`
> > | OPTION | INFO |
> > | :-: | :-: |
> > | --name='名字' | 指定container名字 |
> > | -i | 交互模式運行 |
> > | -t | 使用輸入終端機 |
> > | -d | 背景模式運行 |
> > | -P | 隨機分配映射port |
> > | -p | 指定映射port |
> > | -v="dir/in/host/...:dir/in/container" | 連接Host, Container資料夾 |
> > 
> > > :warning: 若image不存在於本機中，Docker會直接從 Docker Hub [:arrow_down: Pull](#images) 至本機
> > 
> > > :sparkles: -t 時常與 -i 一起使用(-it) \
> > > `$ docker run -it centos /bin/bash`  # /bin/bash 為執行指令
> > 
> > > :sparkles: -p 有4種格式 \
> > > `ip:h_Port:c_Port` \
> > > `ip::c_Port` \
> > > `h_Port:c_Port` \
> > > `cPort`
> >
> > > :sparkles: 使用權限限制
> > > `docker run -it -v dir/in/host/...:dir/in/container:ro [container]`
> >
> > > :warning: 若出現 __cannot open directory .: Permission denied__
> > > 可使用 --privileged=true 參數設置
>
> <br>
> 
> ### ▶ 啟動container
> `$docker start [OPTIONS] [container]`
> 
> | OPTION | INFO |
> | :-: | :-: |
> | -a | 連接container的STDOUT/STDERR |
> | -i | 連接container的STDIN |
> 
> <br>
> 
> ### :page_with_curl: 列出正在運行的container
> `$ docker ps [OPTIONS]`
> > | OPTION | INFO |
> > | :-: | :-: |
> > | -a | 列出所有container (包含已結束) |
> > | -n='數量' | 列出最後n個 |
> > | -l | 列出最後一個 |
> > | -q | 只顯示id |
> > | -s | 顯示文件大小 |
> > | --no-trunc | 完整顯示 |
> 
> <br>
> 
> ### :door:️ 退出當前container
> - 於當前Terminal輸入
> > | METHOD | INFO |
> > | :-: | :-: |
> > | `$ exit` | 結束&退出 |
> > | <kbd>CTRL</kbd>+<kbd>q</kbd>+<kbd>p</kbd> | 不結束&退出 |
> > 
> <br>
>  
> ### :stop_button: 停止container
> `$ docker stop [OPTIONS] [container1] [container2] [...]`
> > | METHOD | INFO |
> > | :-: | :-: |
> > | -t='秒數' | 倒數n秒後停止(default:10) |
> 
> <br>
> 
> ### :knife: 強制停止container
> `$ docker kill [OPTIONS] [container1] [container2] [...]`
> > | OPTION | INFO |
> > | :-: | :-: |
> > | -s='SIGNAL' | 傳送SIGNAL給container |
> 
> <br>
> 
> ### :wastebasket: 刪除container
> `$ docker rm [OPTIONS] [continer1] [container2] [...]`
> > | METHOD | INFO |
> > | :-: | :-: |
> > | -f | 強制刪除進行中的container |
> > | -l | 刪除特定link |
> > | -v | 刪除關於此container的匿名volumes |
> <br>

## <span id="others">3. 其他指令</span>

> ### 📰 列出Log
> `$ docker logs [OPTIONS] [continer]`
> > | METHOD | INFO |
> > | :-: | :-: |
> > | -f | 即時顯示log |
> > | -t | 加入時間戳 |
> > | --tail="n" | 顯示最後 n 筆 |
> <br>
>
> ### ⏳ 查看進程
> `$ docker top [continer]`
>
> <br>
>
> ### 🔍 查看.yml file
> `docker inspect [container]`
> <br>
> 
> ### 🖥 進入運行中的Conatiner
> `docker exec [options] [container] [command]`
> > | OPTION | INFO |
> > | :-: | :-: |
> > | -d | 於背景模式執行command |
> > | -i | 保持STDIN開啟 |
> > | -t | 使用虛擬tty |
> > | -w="..." | 
> > | --env="..."| 設定env var |
> > | --user="..." | 隨機分配映射port |
> >
> > :sparkles: exec 與 attach 差別於
> > exec : 是在 container 中打開新的tty，並可以啟動新的進程
> > attach : 直接進入 container 啟動tty，不會啟動新的進程
> <br>
> 
> ### 📋 複製 Host/Container 資料到 Container/Host
> `docker cp [dir/in/host...] [conatiner]:[dir/in/container]`
> 
> `docker cp [conatiner]:[dir/in/container] [dir/in/host...]`
> <br>