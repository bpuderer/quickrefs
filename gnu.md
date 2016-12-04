Command|Description|Example
---|---|---
alias name='command'|create command shortcut|alias ..='cd ..'
at timespec|read commands from stdin or file and queue for later execution using /bin/sh. atq lists pending jobs and atrm jobnumber deletes job from queue|at now + 1 minutes <<< 'touch /tmp/atdemo'
cp -r srcfile destfile|recursively copy directory|cp -r dir1 dir1_bkup
expand -t 4 filename|convert tabs to 4 spaces|expand -t 4 tabs.txt > spaces.txt
export name=value|set environment variable. export not needed to modify variables already in the environment. e.g. PATH=$PATH:/opt/apache-ant-1.9.7/bin|export FOO=bar
find startingpoint -name pattern -exec command \;|find files and execute command. {} replaced with current file name being processed|find . -name "*.txt" -exec touch {} \;
grep -E 'pattern1&#124;pattern2'|grep with logical or|tail -F server.log &#124; grep -E 'ERROR&#124;FATAL'
grep -ir pattern file|recursive case-insensitive search for pattern|grep -ir "color_scheme" ~/.config
head -n num filename|print first num lines of file|head -n 3 server.log
head -n -num filename|print all but last num lines of file|head -n -3 server.log
kill -9 pid|send SIGKILL to process to cause it to terminate immediately|kill -9 1234
ln -s target linkname|create symlink|ln -s server-1.0.jar server.jar
ls -ltr|list dir contents, oldest first. -l long listing format. -t sort by mod time, newest first. -r reverse sort order. -a include dotfiles. -h human readable sizes. -d list dirs themselves not dir contents. -R list subdirs recursively|ls -ltr
md5sum filename|print MD5 checksum|md5sum geany-1.28.tar.gz
mkdir -p path|created nested directory including parent dirs as needed|mkdir -p ~/games/hacx
netstat -an|print networking info with numeric addresses|netstat -an
nl filename|number lines of files|nl foo.txt
nohup command|ignore SIGHUP when its controlling terminal closed|nohup python httpsim.py >/dev/null 2>&1 &
printenv|print all or specified environment variables|printenv PATH JAVA_HOME
ps -ef|print all processes with full-format listing|ps -ef
rm -rf somedir|recursive delete without prompting|rm -rf ~/wip
rmdir somedir|remove empty directory|rmdir tmpdir
scp -rp srcfile destfile|recursively copy directory|scp -rp somedir user@dest:/path
script filename|typescript of terminal session with timestamp in filename. exit when done|script somefile_\`date +%Y%m%dT%H%M%S\`.log
screen|create screen session. ^a then d to detach screen from terminal|screen
screen -S sessionname|create and name screen session. ^a then d to detach screen from terminal|screen -S upgrade
screen -r sessionname|resume detached screen session|screen -r upgrade
screen -list|print screen sessions|screen -list
sed 's/from/to/g' somefile|replace every instance of "from" with "to" in text file|sed 's/from/to/g' somefile
sed -e 's/from/to/g' -e 's/here/there/g somefile|replace every instance of "from" with "to" and "here" with "there" in text file|sed -e 's/from/to/g' -e 's/here/there/g somefile
seq first increment last|print sequence of numbers. seq last. seq first last. first and increment default to 1|seq 2 3 15
sha1sum filename|print SHA1 checksum|sha1sum geany-1.28.tar.gz > geany-1.28.tar.gz.sha1
sudo -u username command|run command as another user|sudo -u foo ls -l
tac filename|concat and print files in reverse|tac foo.txt bar.txt > baz.txt
tail -n num filename|print last num lines of file|tail -n 3 server.log
tail -n +num filename|print from line num to end of file|tail -n +3 server.log
tail -F filename|output appended data to file and retry if inaccessible|tail -F server.log
tar cvf tarfile filename|collect files into one archive file|tar cvf docs.tar foo.ods bar.kdbx
tar czvf gziptarfile filename|collect files into one archive file and compress with gzip|tar czvf docs.tar.gz ~/Documents
tar tvf tarfile|list contents of archive file|tar tvf docs.tar.gz
tar xvf tarfile|extract tar file|tar xvf file.tar
tar xzvf gziptarfile|extract gzip'd tar file|tar xzvf file.tar.gz
tee filename|read from stdin and write to stdout and file|tail -F server.log &#124; tee test123.log
touch filename|update access and mod time to current time. empty file created if filename does not exist|touch temp.txt
tr -d 'charstodelete'|delete characters from stdin|tr -d '\r' < infile > outfile
uname -a|print system info|uname -a
watch -n numseconds command|continually run command|watch -n 5 ls -l
wc -l|print number of lines|grep -o IOError server.log &#124; wc -l
while true; do command; sleep numseconds; done|continually run command|while true; do ls -l; sleep 5; done
wget url|download file from ftp/http/https|wget http://download.geany.org/geany-1.28.tar.gz

Cron|Description
---|---
*/5 * * * *|every 5 minutes
0,30 * * * *|twice an hour
0 */5 * * *|every 5 hours
0 0 * * *|once a day at midnight

min(0-59) hour(0-23) day of month(1-31) month(1-12) day of week(0-6)(sun-sat)
