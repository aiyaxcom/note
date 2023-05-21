cat /proc/${PID}/cmdline | xargs -0 echo

ps -ef | grep nginx