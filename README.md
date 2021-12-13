# Vader Bond

### Install

```shell
# install virtualenv
python3 -m pip install --user virtualenv
virtualenv -p python3 venv
source venv/bin/activate

pip install eth-brownie
pip install matplotlib
pip install numpy

brownie pm install OpenZeppelin/openzeppelin-contracts@3.4.2

npm i
npm i -g ganache-cli

cp .env.sample .env
```

### Test

```shell
brownie test tests/path-to-test-file-or-folder -s -v

# mainnet
npx ganache-cli \
--fork https://mainnet.infura.io/v3/$WEB3_INFURA_PROJECT_ID \
--unlock $ETH_VADER_LP_WHALE

env $(cat .env) brownie test tests/mainnet/test_zap_eth.py --network mainnet-fork -s
```

### Deploy

```shell
brownie run scripts/deploy_treasury.py --network kovan
brownie run scripts/deploy_bond.py --network kovan
```

### Simulation

##### Increasing bond price

![bond-price-inc](./doc/bond-price-inc.png)

##### Decreasing bond price

![bond-price-dec](./doc/bond-price-dec.png)

### Deployment

1. Deploy `Treasury`
2. Deploy `VaderBond`
3. Call `Treasury.setBondContract`

##### Kovan

-   LP: [0x38F19a5452B03262203cAe9532Fbfd211fa32FF1](https://kovan.etherscan.io/address/0x38F19a5452B03262203cAe9532Fbfd211fa32FF1)
-   Vader: [0x1fd03e4eA209497910fACE52e5ca39124ef2E8BE](https://kovan.etherscan.io/address/0x1fd03e4eA209497910fACE52e5ca39124ef2E8BE)
-   Treasury: [0x15d89713eA5C46dE381C51A34fE4C743677576B4](https://kovan.etherscan.io/address/0x15d89713eA5C46dE381C51A34fE4C743677576B4)
-   Bond: [0x66BcC1c537509bA441ccc9DF39E18CC142C59775](https://kovan.etherscan.io/address/0x66BcC1c537509bA441ccc9DF39E18CC142C59775)

### Misc

```shell
pip3 install solc-select

# select solc compiler
solc-select install 0.7.6
solc-select use 0.7.6

# check code size (max 2457 bytes)
brownie compile -s
```
