Command|Description|Example
---|---|---
alias name='command'|create command shortcut|alias ..='cd ..'
find startingpoint -name pattern -exec command \;|find files and execute command. {} replaced with current file name being processed|find . -name "*.txt" -exec touch {} \;
grep -E 'pattern1&#124;pattern2'|grep with logical or|tail -F server.log &#124; grep -E 'ERROR&#124;FATAL'
grep -ir pattern file|recursive case-insensitive search for pattern|grep -ir "color_scheme" ~/.config
ln -s target linkname|create symlink|ln -s server-1.0.jar server.jar
netstat -an|print networking info with numeric addresses|netstat -an
ps -ef|print all processes with full-format listing|ps -ef
scp -rp srcfile destfile|recursively copy entire directory|scp -rp somedir user@dest:/path
script filename|typescript of terminal session with timestamp in filename. exit when done|script somefile_\`date +%Y%m%dT%H%M%S\`.log
sed 's/from/to/g' somefile|replace every instance of "from" with "to" in text file|sed 's/from/to/g' somefile
sed -e 's/from/to/g' -e 's/here/there/g somefile|replace every instance of "from" with "to" and "here" with "there" in text file|sed -e 's/from/to/g' -e 's/here/there/g somefile
sudo -u username command|run command as another user|sudo -u foo ls -l
tail -F filename|output appended data to file and retry if inaccessible|tail -F server.log
tar xvf tarfile|extract tar file|tar xvf file.tar
tar xzvf gziptarfile|extract gzip'd tar file|tar xzvf file.tar.gz
tar cvf tarfile|create tar file|tar cvf file.tar somedir
tar czvf gziptarfile|create gzip'd tar file|tar czvf file.tar.gz somedir
tee filename|read from stdin and write to stdout and file|tail -F server.log &#124; tee test123.log
touch filename|update access and mod time to current time. empty file created if filename does not exist|touch temp.txt
tr -d 'charstodelete'|delete chars from stdin|tr -d '\r' < infile > outfile
watch -n numseconds command|continually run command|watch -n 5 ls -l
while true; do command; sleep numseconds; done|continually run command|while true; do ls -l; sleep 5; done
wget url|download file from ftp/http/https|wget http://download.geany.org/geany-1.28.tar.gz
