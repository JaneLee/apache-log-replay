# Script to replay HTTP requests from an Apache access logfile

Features

- Takes the time between requests into account
- Replaying can be sped up by a given factor
- Optionally send all requests to a selected (proxy) server
- Support multiple threads to simulate concurrence scenario at testing environment
- Support filtering invalid requests during replaying online request
    - ignorelist.txt（日志文件中无效的请求串列表，
    会在日志文件解析过程中自动将指定的请求串们直接过滤掉。回放阶段就可以不回放这些）

## Installation

Requires Python >= 2.6

Simply download the file and execute it...

## Usage

    Usage: apache-log-replay.py [options] logfile
    
    Options:
      -h, --help            show this help message and exit
      -p PROXY, --proxy=PROXY
                            send requests to server PROXY
      -s SPEEDUP, --speedup=SPEEDUP
                            make time run faster by factor SPEEDUP
      -t MULTIPLE THREADS COUNT
                            specify the count of multiple threads to simulate concurrence scenario at testing environment
      -i INTERVAL
                            specify the interval beturn each thread
                            
## OTHER HELPFUL TIPS
- 线上的access日志可能会很大，解析过程都可能会很久。可以使用这个命令将线上access日志拆分成多个小日志文件：
    命令： split -l 10000 log
    > 10000是指按1w行进行分割
    > 会生成xa*为文件名的很多小文件
- 请确认你的线上日志文件中请求串的位置，及分割符。
  目前工具中使用“ “空格进行split日志，配置在文件的前面，可直接修改该全局变量即可
