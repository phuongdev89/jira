
# jira

[README](README.md)


+ Long Term Support Version(arm64&amd64): v9.12.14
+ Latest Version(arm64&amd64): v9.17.4
+ Beta Version(arm64&amd64): v10.1.1
+ [The new way](https://github.com/haxqer/jira/tree/build-your-own) of use allows you to conveniently upgrade and modify parameters on your own, and it offers convenient support for HTTPS (thanks to [xsharp](https://github.com/xsharp)).

New Confluence/Jira releases support only Data Center licenses. To generate a Data Center licenses, add the `-d` parameter.

default port: `8080`

## requirement
- docker: 17.09.0+
- docker-compose: 1.24.0+
- do not update `jira software` or `jira core`

## How to run with docker-compose

- clone jira

```
git clone https://github.com/phuongdev89/jira.git && cd jira && git checkout release
```

- start jira & mysql daemon

```
docker-compose up -d
```
## Setup Jira
1. choose `I'll set it up myself`
2. Database setup `My Own Database`:
 - driver: `Mysql 8.0`
 - host: `mysql-jira`
 - port: `3306`
 - database: `jira`
 - username: `root`
 - password: `123456`

## How to hack jira

Run in docker `jira-srv`

```
export SERVER_ID=server_id_that_showed_when_installed
java -jar /var/agent/atlassian-agent.jar -d -p jira -m $ACTIVE_MAIL -n $ACTIVE_NAME -o $ACTIVE_ORG -s $SERVER_ID
```

## How to hack jira plugin

- .eg I want to use BigGantt plugin
1. Install BigGantt from jira marketplace.
2. Find `App Key` of BigGantt is : `eu.softwareplant.biggantt`
3. Execute :

```
export SERVER_ID=server_id_that_showed_when_installed
java -jar /var/agent/atlassian-agent.jar -d -p eu.softwareplant.biggantt -m $ACTIVE_MAIL -n $ACTIVE_NAME -o $ACTIVE_ORG -s $SERVER_ID
```

4. Paste your license


## Hack Jira Service Management(jsm) Plugin

Thanks to:
+ [d1m0nstr](https://github.com/d1m0nstr) for [Jira Service Management](https://github.com/haxqer/jira/issues/11)

```
export SERVER_ID=server_id_that_showed_when_installed
java -jar /var/agent/atlassian-agent.jar -d -p jsm -m $ACTIVE_MAIL -n $ACTIVE_NAME -o $ACTIVE_ORG -s $SERVER_ID
```

