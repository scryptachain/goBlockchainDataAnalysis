# goBlockchainDataAnalysis
blockchain data analysis, written in Go

#### Not finished - ToDo list
To Do list in DevelopmentNotes.md https://github.com/arnaucode/goBlockchainDataAnalysis/blob/master/DevelopmentNotes.md

## Instructions

### Install
1. Nodejs & NPM https://nodejs.org/ --> to get npm packages for the web
2. MongoDB https://www.mongodb.com/
3. lyra wallet https://download.lyra.world/, or the Cryptocurrency desired wallet
4. goBlockchainDataAnalysis https://github.com/arnaucode/goBlockchainDataAnalysis

### Configure
- Wallet /home/user/.lyra/lyra.conf:
```
rpcuser=lyrarpc
rpcpassword=password
rpcport=3021
rpcworkqueue=2000
server=1
rpcbind=127.0.0.1
rpcallowip=127.0.0.1
```

- goBlockchainDataAnalysis/config.json:
```json
{
    "user": "lyrarpc",
    "pass": "password",
    "host": "127.0.0.1",
    "port": "42223",
	"genesisTx": "2346f9c436d961bf4f5a3818f60154e15ddd056d59f05b270240d0837d15daa5",
	"genesisBlock": "e2aacf31ce196903e00157a50d207d04a152176b4eb83ecbb0b75b0c9455d1fd",
    "startFromBlock": 0,
    "server": {
        "serverIP": "127.0.0.1",
        "serverPort": "3014",
        "webServerPort": "8080",
        "allowedIPs": [
            "127.0.0.1"
        ],
        "blockedIPs": []
    },
    "mongodb": {
        "ip": "127.0.0.1",
        "database": "goBlockchainDataAnalysis"
    }
}
```

### Run

1. Start MongoDB
```
sudo service mongod start
```

2. Start wallet
```
./lyrad -txindex -reindex-chainstate
```
Wait until the entire blockchain is downloaded.

3. Run explorer, to fill the database
```
./goBlockchainDataAnalysis -explore
```

    3.1. The next runs, once the database have data and just need to add last blocks added in the blockchain, can just run:
```
./goBlockchainDataAnalysis -continue
```

    3.2. If don't want to fill the database, can just run:
```
./goBlockchainDataAnalysis
```

Webapp will run on 127.0.0.1:8080

4. ADDITIONAL - Run the webserver, directly from the /web directory
This can be useful if need to deploy the API server in one machine and the webserver in other.
In the /web directory:
```
npm start
```
Webapp will run on 127.0.0.1:8080



### Additional info
- Backend
    - Go lang https://golang.org/
    - MongoDB https://www.mongodb.com/
- Frontend
    - AngularJS https://angularjs.org/
    - Angular-Bootstrap-Material https://tilwinjoy.github.io/angular-bootstrap-material


### Some screenshots
Some screenshots can be old, and can contain errors.

![goBlockchainDataAnalysis](https://raw.githubusercontent.com/arnaucode/goBlockchainDataAnalysis/master/screenshots/goBlockchainDataAnalysis00.png "goBlockchainDataAnalysis")

![goBlockchainDataAnalysis](https://raw.githubusercontent.com/arnaucode/goBlockchainDataAnalysis/master/screenshots/goBlockchainDataAnalysis01.png "goBlockchainDataAnalysis")

![goBlockchainDataAnalysis](https://raw.githubusercontent.com/arnaucode/goBlockchainDataAnalysis/master/screenshots/goBlockchainDataAnalysis02.png "goBlockchainDataAnalysis")

![goBlockchainDataAnalysis](https://raw.githubusercontent.com/arnaucode/goBlockchainDataAnalysis/master/screenshots/goBlockchainDataAnalysis03.gif "goBlockchainDataAnalysis")
