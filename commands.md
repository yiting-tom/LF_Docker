[2. 常用指令](#command)
> [i. images](#images)  
> [ii. container](#container)
***

# <span id="command">常用指令</span>

## <span id='images'>images</span>

### 1.  :mag: 在[Docker hub](https://hub.docker.com/)上搜尋images
`$ docker search [OPTIONS] [image:tag]`
> | OPTION | INFO |
> | :-: | :-: |
> | -s='星數' | 星星數量需大於多少 |
> | --no-trunc | 列出完整訊息 |
> | --automated | 只列出 automated build 的 image |

<br>

### 2. :arrow_down: 將images從[Docker Hub](https://hub.docker.com/)下載至本機
`$ docker pull [image1:tag1] [image2:tag2][...]`  
> | OPTION | INFO |
> | :-: | :-: |
> | -f | 使用[過濾器](https://docs.docker.com/engine/api/v1.40/#operation/ImageList) |

<br>  

### 3.:page_with_curl: 列出本機所有images
`$ docker images [OPTIONS]`  
> | OPTION | INFO |
> | :-: | :-: |
> | -q | 只列出 image id |
> | -a | 列出中間層 images |
> | --digests | 列出摘要訊息 |
> | --no-trunc | 列出完整訊息 |

<br>

### 4. :wastebasket: 刪除本機images
`$ docker rmi [image1:tag1] [image2:tag2] [...]`  
> | OPTION | INFO |
> | :-: | :-: |
> | -f | 強制刪除 |
> | --no-prune | 不刪除沒有tag的parent images |
> 
> <font size=2>:sparkles: 刪除所有本機images \
> `$ docker rmi $(docker images -qa)` \
> </font>

<br>

## <span id='container'>container</span>  

### 1. ️:runner: 創建並啟動container
`$ docker run [OPTIONS] [image:tag] [COMMAND] [args]`
> | OPTION | INFO |
> | :-: | :-: |
> | --name='名字' | 指定container名字 |
> | -i | 交互模式運行 |
> | -t | 使用輸入終端機 |
> | -d | 背景模式運行 |
> | -P | 隨機分配映射port |
> | -p | 指定映射port |
> 
> :warning: 若image不存在於本機中，Docker會直接從[Docker Hub](https://hub.docker.com) [:arrow_down:Pull](#images)至本機
> 
> <font size=2>\
> :sparkles: -t 時常與 -i 一起使用(-it) \
> `$ docker run -it centos`
> 
> :sparkles: -p 有4種格式 \
> `ip:h_Port:c_Port` \
> `ip::c_Port` \
> `h_Port:c_Port` \
> `cPort`
> </font>

<br>

### 2. ▶ 啟動container
`$docker start [OPTIONS] [container]`

| OPTION | INFO |
| :-: | :-: |
| -a | 連接container的STDOUT/STDERR |
| -i | 連接container的STDIN |

<br>

### 3. :page_with_curl: 列出正在運行的container
`$ docker ps [OPTIONS]`
> | OPTION | INFO |
> | :-: | :-: |
> | -a | 列出所有container (包含已結束) |
> | -n='數量' | 列出最後n個 |
> | -l | 列出最後一個 |
> | -q | 只顯示id |
> | -s | 顯示文件大小 |
> | --no-trunc | 完整顯示 |


<br>

### 4. :door:️ 退出當前container
- 於當前Terminal輸入
> | METHOD | INFO |
> | :-: | :-: |
> | `$ exit` | 結束&退出 |
> | <kbd>CTRL</kbd>+<kbd>q</kbd>+<kbd>p</kbd> | 不結束&退出 |
> 
<br>
 
### 5. :stop_button: 停止container
`$ docker stop [OPTIONS] [container1] [container2] [...]`
> | METHOD | INFO |
> | :-: | :-: |
> | -t='秒數' | 倒數n秒後停止(default:10) |

<br>

### 6. :knife: 強制停止container
`$ docker kill [OPTIONS] [container1] [container2] [...]`
> | OPTION | INFO |
> | :-: | :-: |
> | -s='SIGNAL' | 傳送SIGNAL給container |

<br>

### 7. :wastebasket: 刪除已停止的container
`$ docker rm [OPTIONS] [continer1] [container2] [...]`
> | METHOD | INFO |
> | :-: | :-: |
> | -f | 強制刪除進行中的container |
> | -l | 刪除特定link |
> | -v | 刪除關於此container的匿名volumes |
<br>