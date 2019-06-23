#Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
#For more information, please see http://aka.ms/containercompat 

FROM microsoft/aspnet:4.7.2-windowsservercore-1803
ARG source

WORKDIR C:/newrelic

RUN net start MSIServer ;\
	Invoke-WebRequest -Uri "https://download.newrelic.com/dot_net_agent/latest_release/NewRelicDotNetAgent_x64.msi" -OutFile "C:\newrelic\newrelic-agent.msi" ;\
	msiexec /i C:\newrelic\newrelic-agent.msi /l C:\newrelic\newrelic.log NR_LICENSE_KEY=REMOVED ;\
	IISRESET

WORKDIR /inetpub/wwwroot
COPY . .
EXPOSE 80