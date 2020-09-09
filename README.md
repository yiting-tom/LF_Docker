<div align=center><a href="https://www.docker.com/"><img src="https://www.docker.com/sites/default/files/social/docker_facebook_share.png" style="width:30%"></a></div>

# 目錄
[A. 簡介](#concept)
> [1. Docker 的誕生](#dockers-born)  
> [2. Docker 的理念](#what-is-docker)  
> [3. Docker 的優勢](#what-can-docker-do)  
> [4. Docker 的組成](#three-elements)
> 

# <span id="concept">簡介</span>
## 1. <span id="dockers-born">Docker 的誕生</span>
> __產品開發__ 與 __運營維護__ 間的協作，需要關心許多事件 \
> 其中包含了ＯＳ、環境、參數配置等等，其中只要一項不相同，就有可能導致預期外的事件發 :fire:

:question: 那可不可以將 __專案與環境一起__ 傳到目標機器，再打開就好？
<hr> 
<br>

## 2. <span id="what-is-docker">Docker 的理念</span>
> __"Build, Ship, Run, Any App Anywhere" 「一次封裝，隨處運行」__ \
> Docker 在 Linux Container 的基礎上發展而來，並將 App 運行在 Docker Container 上\
> 且 Docker Container 於任何系統上都是一致的，因此。。。
> 
> __「只需要配置一次環境，換到其他機器上就可一鍵部署」__ 😁
> ![docker_concept](https://img.itw01.com/images/2017/11/30/11/0432_95AUpJ_GZXPEGJ.jpg!r800x0.jpg)
<hr>
<br>

## 3. <span id="what-is-docker">Docker 的優勢<span> 
> __Virture Machine (VM)__ 就是一種可攜帶環境的解決方案\
> &nbsp; 但傳統 VM 的缺點： \
> &nbsp; 1.佔用資源多 2.啟動超慢 3.步驟冗余
> 
> __Linux Containers (LXC)__ 是由 Linux 發展出的另一種虛擬化技術 \
> &nbsp; LXC 與 VM 最大差別在於，LXC __不是模擬整個OS__，而是將 processes 隔離 \
> &nbsp; 如此一來就可以將需要的環境、資源與設置等，封裝到一個 Container 中， \
> &nbsp; 需要哪項服務就使用哪個 Container，不必將整個OS一起包起來。 \
> &nbsp; 系統因此變得高效、輕量，並保證在任何環境中都能提供相同的服務 
> 
> ![docker_vs_vm](https://miro.medium.com/max/4932/1*tAAJ06mUHOwpRH7R5R9oeA.png)
<hr>
<br>

## 4. <span id="what-is-docker">Docker 的組成</span>
> - __image :__ 
> READONLY 的模板，被用來創建 Container，可被重複使用
<br>
> - __container :__
> 可想像成一個簡易的 Linux 環境，可被 _run_ , _start_ , _stop_ , _rm_ 每個 Container 相互隔離，以保證不被彼此影響
<br>
> - __repository :__
> 集中存放 image 的倉庫
<br>
> - __registry :__
> 存放 repository 的大倉庫
<br>
> ![docker-architecture](https://wiki.aquasec.com/download/attachments/2854889/Docker_Architecture.png?version=1&modificationDate=1520172700553&api=v2)
> 1. Docker 本身是一個管理引擎，將 Application 和環境配置封裝形成一個 image，通過這個 image 可以產生多個 container
<br>
> 2. 一個 container 運行一種服務，當需要使用某服務，就可以透過 Docker Client 創建一個相應的運行環境，並提供服務
<hr>
<br>

## 5. <span id="what-is-docker">什麼是 Docker?</span>
