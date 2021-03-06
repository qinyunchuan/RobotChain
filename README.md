# RobotChain
## Installation

1. Make sure [Python 3.6+](https://www.python.org/downloads/) is installed. 
2. Install [pipenv](https://github.com/kennethreitz/pipenv). 

```
$ pip install pipenv 
```

3. Create a _virtual environment_ and specify the Python version to use. 

```
$ pipenv --python=python3.6
```

4. Install requirements.  

```
$ pipenv install 
``` 

5. Run the server:
    * `$ pipenv run python blockchain.py` 
    * `$ pipenv run python blockchain.py -p 5001`
    * `$ pipenv run python blockchain.py --port 5002`
    

## Architecture
![Image text](https://github.com/qinyunchuan/RobotChain/blob/master/image/robotchain.png)
Key Assignment:
```
Owner Key:PKo,SKo
Operator Party Key:PKp,SKp
Manufacture Key: PKm,SKm
Robot Key:PKr,SKr
```
Right Map
```
{
"Robot":"PKr",
"Role":["Owner","Administrator","Operator"],
"Owner":["CMD1","CMD2","CMD3"]，
"Administrator"：["CMD1","CMD2"]，
"Operator"：["CMD1"]，
}
```

Command Flow
```
Owner->Robot( Owner->Operator->（Check Ledger）->Ledger->Operator->Robot ）
Sign: SKo(PKp,PKr,CMD) //CMD is public unavailable

Robot->Owner( Robot->Operator->Ledger->Operator->Owner ）
Sign:SKr(PKp,PKo,Result)
```

Ledger Format:
```All Parties should log operations for audit
 'sender': sender,
 'recipient': recipient,
 'cmd': Hash(SKo(PKp,PKr,CMD)),
 'amount':number  #Add Robot will decrease the sender's amount
```