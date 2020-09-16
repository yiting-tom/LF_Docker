# 目錄
[A. 簡介](./README.md)
> [1. Docker 的誕生](./README.md)  
> [2. Docker 的理念](./README.md)  
> [3. Docker 的優勢](./README.md)  
> [4. Docker 的組成](./README.md)

[B. 常用指令](commands.md)  
> [1. images](#images)  
> [2. container](#container)  
> [3. others](#others)

[C. Docker File](#docker-file)  
> [1. Docker File 是什麼及如何使用](#what-is-df)  
> [2. Docker File 保留字指令](#df-tags)  
> [3. Docker File 撰寫](#df-script)  
> [4. Docker File 部署](#df-build)  

# Docker File
![df-graph](https://quppler.com/wp-content/uploads/2019/03/DockerComponents.png)

***

## <span id='what-is-df'>1. Docker File 是什麼及如何使用</span>
#### `Docker File 是被用來建構(build) image 的 script file`

#### 基礎知識：
> 1. 每個保留字都是 __大寫__
> 2. 每個保留字後面加上 __至少一個參數__
> 3. __\#__ 表示註解
> 4. 每條指令都會 __創建新的 image 層__

#### docker 執行 docker file 的流程：
> ![layer-by-layer](https://dzone.com/storage/temp/13029811-1581358050914.png)
> 1. 從基礎 images run 一個 container
> 2. 執行一條指令，並修改此 container
> 3. 執行類似 docker commit，提交新的 image layer
> 4. 基於新提交的 image 運行新的 container
> 5. 重複步驟 3. 4. 直到所有指令都完成

***

## <span id='df-tags'>2. Docker File 保留字指令</span>
> ![cheat-sheet](https://extremeautomation.io/img/cheatsheets/cheat_sheet_docker_page_1.png)
> | COMMAND | INFO |
> | :-: | :-: |
> | FROM | 基礎 image |
> | MAINTAINER | 作者name, mail |
> | RUN | container 建構時進行的命令 |
> | EXPOSE | container 的對外 port |
> | WORKDIR | container 進入後的位置 |
> | ENV | 設置 env 變數 |
> | ADD | 將 host 文件複製並解壓至 container |
> | COPY | 將 host 文件複製至 container |
> | VOLUME | container 數據儲存 volume |
> | CMD | container 啟動時的要運行的命令 |
> | ENTRYPOINT | 目的與 CMD 相同 |
> | ONBUILD | 使用於繼承中，當 parent 被繼承後觸發 |

## <span id='df-script'>3. Docker File 撰寫</span>
> ``` docker
> # using alpine be the base image
> FROM alpine:3.9
> # adding maintainer
> MAINTAINER someone<someone@mail>
> 
> # install vim
> RUN apk add vim
> # copy host:./test_file to container:/test_file
> ADD ./test_file /test_file
> # config env arg TEST to /test_file
> ENV TEST /test_file
> 
> # print success hint
> RUN echo "--------- success ---------"
> # execute ash shell
> CMD /bin/ash
> ```

## <span id='df-build'>4. Docker File 部署</span>

> ### Build to images
> > #### `$ docker build [options] [image:tag] [dockerfile]`
> > ![df_build](/screenshot/df_build.png)
> >
> > <br>
> >
> > #### `$ docker images`
> > ![df_images](/screenshot/df_images.png)
> >
> > <br>
> 
> ### Run on container
> > #### `$ docker run [options] [image:tag]`
> > ![df_run](/screenshot/df_run.png)
> >
> > ![df_check](/screenshot/df_check.png)
> > <br>