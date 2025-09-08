OOM kill 우선순위(OOM떴을때, 뭐부터 먼저 죽일까~?)
어떤 프로세스를 먼저 줄일지에 대한 지표가 되는게 **oom_adj**(=oom_score_adj)

```
TOMCAT_PID=`ps -ef | grep "^.*/bin/java -Djava.util.logging.config.file=/usr/local/tomcat/conf/logging.properties.*$" | grep -v 'grep'| awk '{print $2}'`

if [ ! -z $TOMCAT_PID ];then
        echo "TOMCAT_PID::$TOMCAT_PID"
#cat /proc/$TOMCAT_PID/oom_adj
        echo pwd | sudo -S bash -c "echo '-17' | tee /proc/$TOMCAT_PID/oom_adj";
else
        echo "TOMCAT NOT RUNNING...."
fi
```


`/proc/PID/oom_adj` 에 kill 순서값이 적혀있음~