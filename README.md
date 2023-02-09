# MANGO - 4
접두사 - 망고야

원본:https://github.com/RileCraft/DiscordBot-Template
# ChatCommands
ChatCommands 기본 형식
```
const { ButtonBuilder, ActionRowBuilder,EmbedBuilder } = require("discord.js")
const favorability = require("../function/favorability")
const talkedRecently = new Set()
module.exports = {
    name: "명령어",
    aliases: ["별칭"],
    run: async(client, message) => {
      const f = await favorability.add(talkedRecently,message.author.id,1)
      if(f==false){
        message.channel.send(`no`)
      }else{
        message.channel.send(`bye / favorability + 1`)
      }
      
    }
}
```

# 함수 사용
반환 하는 함수일때 const data = await .... 필수
* customcommand.js
```
const customcommand = require("./customcommand")
```
```
customcommand.add("들어온 커맨드","나갈 대사",유저 태그,유저 id);
반환 : X
```
```
customcommand.find("커맨드 이름","유저 id");
반환 : 
값이 true일때 - indata(들어온 커맨드), outdata(나갈 대사), member(유저 태그)
값이 false일때 - false
```

* favorability.js
```
const favorability = require("./favorability")
```
```
favorability.add(new Set(),"유저 id",올라갈 호감도)
반환 : 
값이 true일때 - fnumber(총 호감도)
값이 false일때 - false
```
```
favorability.find("유저 id")
반환 : 
값이 true일때 - fnumber(총 호감도)
값이 false일때 - false
```

* userdata.js
```
const userdata = require("./userdata")
```
```
userdata.prove("유저 id");
반환 : 
값이 true일때 - true
값이 false일때 - false
```
```
joindata.createjoindata("유저 id","메세지 id","채널 id");
반환 : X
```

* joindata.js
```
const joindata = require("./joindata")
```
```
joindata.findjoindata("유저 id");
반환 : 
값이 true일때 - userid(유저 id), msgid(메세지 id), chid(채널 id)
값이 false일때 - false
```
```
joindata.deljoindata("유저 id");
반환 : X
```
```
joindata.createjoindata("유저 id","메세지 id","체널 id");
반환 : X

```

* pool.js
```
const poolname = require("./pool")
```
```
poolname.conn()
반환 : pool
```

# DB
사용DB : maria DB
Credentials/DB.js에서 DB설정 가능

봇 DB기본설정
```
host: 'localhost'
port: 3306
user: 'root' 
password: '    '
database:"mango"
```

# HeidiSQL 설정
```
mango
└ joindata
  └ userid
  └ msgid
  └ chid
└ userdata
  └ userid
  └ date
└ command
  └ indata
  └ outdata
  └ member
  └ id 
  └ date
```
  
![image](https://user-images.githubusercontent.com/98867089/194068368-832be19e-96e0-48d5-b3be-c6cd923e1052.png)

![image](https://user-images.githubusercontent.com/98867089/194068454-c30cf9bb-fca2-4eb6-b188-fc645b4da9ac.png)

![image](https://user-images.githubusercontent.com/98867089/194215189-a3d156c8-950c-4786-903b-7949edd1da13.png)
