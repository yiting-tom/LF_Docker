<div align=center><img src="https://www.docker.com/sites/default/files/social/docker_facebook_share.png" style="width:30%"></div>

# 目錄
[1. 簡介](#concept)
> [i. 什麼是 Docker?](#what-is-docker)

[2. 常用指令](#command)
> [i. images](#images)  
> [ii. containers](#containers)
***

### <span id="command">常用指令</span>

#### <span id='images'>images</span>

##### 1.  在[docker hub](https://hub.docker.com/)上搜尋images
`$ docker search [OPTIONS] [image_name]:[tag (default=latest)]`

| OPTION | INFO |
| :-: | :-: |
| -s='星數' | 星星數量需大於多少 |
| --no-trunc | 列出完整訊息 |
| --automated | 只列出 automated build 的 image |

<br>

##### 2. 將images從[Docker Hub](https://hub.docker.com/)下載至本機
`$ docker pull [image]:[tag (default=latest)]`  
| OPTION | INFO |
| :-: | :-: |
| -f | 使用[過濾器](https://docs.docker.com/engine/api/v1.40/#operation/ImageList) |

<br>  

##### 3. 列出本機所有images
`$ docker images [OPTIONS]`  
| OPTION | INFO |
| :-: | :-: |
| -q | 只列出 image id |
| -a | 列出中間層 images |
| --digests | 列出摘要訊息 |
| --no-trunc | 列出完整訊息 |

<br>



### <span id="concept">簡介</span>
##### 1. <span id="what-is-docker">What is Docker?</span>

   
![docker_concept](https://hackernoon.com/images/4x5x32di.jpg)




