# Meschedule
A scheduler based on time and dependencies on UNIX/Linux



### Installation

Clone and install [Melang](https://github.com/Water-Melon/Melang), then clone this repository, the installation is done.



### Run

```shell
$ melang scheduler.mln
```



### Scheduler Configuration

```
{
    "path": "test", //task directory path
    "concurrency": 10, //the number of workers to execute shell command
    "delta_sec": 15, //set cron task start second per minute
    "data": {} //customized variables to replace the relevant keys in the command of a task configuration
}
```



### Task Configuration

```
{
    "name": "task name",
    "period": "* * * * *", //cron format but not support range '-', such as 1-10.
    "deps": [],//dependencies, these are strings relate to task names
    "cmd": "shell command",
    "data": {}
}
```

Example:

```
{
    "name": "a", //this task's name.
    "period": "* * * * *", //execute in every minute.
    "deps": ["b", "c"], //depends on task b and c, which means b and c will be execute before a if they are scheduled in the same time.
    "cmd": "echo CMD", //CMD can be found in data. this command is "echo a".
    "data": {
        "CMD": "a"
    }
}
```
