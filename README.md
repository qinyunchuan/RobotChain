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
Owner Key:PKo,SKo
Operator Party Key:PKp,SKp
Manufacture Key: PKm,SKm
Robot Key:PKr,SKr

Owner->Robot( Owner->Operator->Ledger->Operator->Robot ）
Sign: SKo(PKp,PKr,CMD) //CMD is public available
Robot->Owner( Robot->Operator->Ledger->Operator->Owner ）
Sign:SKr(PKp,PKo,Result)
