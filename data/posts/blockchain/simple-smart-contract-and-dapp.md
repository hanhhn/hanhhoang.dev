---
title: 'Hello word dApp - smart contract'
date: '2022-05-16'
tags: ['blockchain', 'web3', 'dApp']
draft: false
summary: 'Hướng dẫn tạo một ứng dụng dApp đơn giản với: Reactjs, Ethers.js, Metamask, Smart contract, alchemy'
---

## Giới thiệu

Hướng dẫn tạo mội ứng dụng dApp đơn giản với: Reactjs, Ethers.js, Metamask, Smart contract, Alchemy, Hardhat

Bài viết không đi sau vào giới thiệu các lib mà chỉ hướng dẫn tạo một dapp và một smart contract. EDI không thể thiếu là visual studio code =))

> Reactjs - Là một lib UI

> Ethers.js - Là một lib giúp chúng ta tương tác với ethereun network

> Metamark - Là một wallet

> Smart Contract - Là một chương trình chạy trên blockchain network

> Alchemy - Thay vì phải dựng lên 1 node cho mạng lưới blockchain, thì có thể sử dụng alchemy.

> Hardhat - Tool build solidity trên js

## Tạo Smart Contract (step by step)

### Step 1 - Tạo app trên Alchemy

`Lưu ý`: Nếu không sử dụng Alchemy thì có thể sử dụng third party khác cũng cho phép tương tác với network. Tìm hiểu thên theo [link](https://docs.ethers.io/v5/api-keys/)

- Đăng ký theo link sau [https://www.alchemy.com](https://alchemy.com/?r=TM0NjkyMzg3MTYwN)
- Create app - Chọn network `Goerli` nhé
  ![Tạo app](https://raw.githubusercontent.com/hanhhn/hanhhoang.dev/master/public/images/simple-smart-contract-and-dapp/1.png)
- Lấy api key - Api key trong hình chỉ là hàng test
  ![Lấy api key](https://raw.githubusercontent.com/hanhhn/hanhhoang.dev/master/public/images/simple-smart-contract-and-dapp/2.png)

`Goerli` trong lúc viết tut này thì chỉ có testnet `Goerli` là đang run, ko sử dụng testnet này thì cũng có thể sử dụng 1 testnet khác

### Step 2 - Tạo một wallet ở metamask

`Lưu ý` Ai chưa có hay đã có rồi cũng nên tạo 1 Wallet mới để test nhé, tránh dùng ví chính lộ private key. Tạo wallet dễ ợt à, anh/em tự tạo nhé. Khi tạo xong nhớ switch qua testnet `Goerli`

### Step 3 - Kiếm ETH cho test account vừa tạo

Có nhiều trang kiếm ETH cho testnet lắm. Các bạn google phát là ra. Sau đó chuyển eth cho ví test. Mình xài web https://goerlifaucet.com/ để get ETH, Login vào thì get dc nhiều ETH hơn.

![get eth](https://raw.githubusercontent.com/hanhhn/hanhhoang.dev/master/public/images/simple-smart-contract-and-dapp/4.png)

### Step 4 - Coding simple smart contract

1. Init project react js

```
npx create-react-app dapp-stored-message
cd dapp-stored-message
npm start
```

2. Install hardhat & Create Hardhat project

```
npm install --save-dev hardhat
npx hardhat
```

Nhớ chọn `❯ Create an empty hardhat.config.js`

```
mkdir contracts //thư mục này để viết smart contract *.sol
mkdir scripts //thư mục này để chứ script deploy
```

3. hardhat.config.js & .env

```
npm install dotenv --save
npm install --save-dev @nomiclabs/hardhat-ethers "ethers@^5.0.0"
```

`Your environment file must be named .env or it won't be recognized as an environment file. Do not name it process.env or .env-custom or anything else.`

```:.env
API_URL = "https://eth-goerli.alchemyapi.io/v2/5D0VF_1ogSYMSaNrwxxKwQsLS84SILH9" // đổi api key lại nhé
PRIVATE_KEY = "" // cái này là private key wallet của bạn, kiếm rồi bỏ zo nhé
API_KEY = "5D0VF_1ogSYMSaNrwxxKwQsLS84SILH9" // đổi api key lại nhé
```

```js:hardhat.config.js
require("dotenv").config();
require("@nomiclabs/hardhat-ethers");

const { API_URL, PRIVATE_KEY } = process.env;

module.exports = {
  defaultNetwork: "goerli",
  networks: {
    hardhat: {},
    goerli: {
      url: API_URL,
      accounts: [`0x${PRIVATE_KEY}`], // chổ này lưu ý phải bắt đầu 0x trước private key nhé
    },
  },
  solidity: "0.8.4",
  paths: {
    sources: "./contracts",
  },
};
```

4. Coding smart contract - HelloKitty.sol
   Tạo file Hello-Kitty.sol ở folder ./contracts

```sol
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.8.4;
contract HelloKitty {
    event UpdatedMessages(string oldStr, string newStr);

    string public message;

    constructor(string memory initMessage) {
        message = initMessage;
    }

    function setMessage(string memory newMessage) public {
        string memory oldMsg = message;
        message = newMessage;
        emit UpdatedMessages(oldMsg, newMessage);
    }

    function getMessage() public view returns (string memory) {
        return message;
    }
}
```

Easy phải không =)) 5. compile smart contract

```
npx hardhat compile
```

Compile thành công và không lỗi lầm gì thì sẽ sinh ra 2 folder: artifacts, cache. Ở đây mình chỉ care tới artifacts vì có chứa thông tin abi 6. Viết script deploy
Tạo file /scripts/deploy.js

```js:deploy.js
const hre = require("hardhat");

async function main() {
  // We get the contract to deploy
  const Hello = await hre.ethers.getContractFactory("HelloKitty");
  const helloContract = await Hello.deploy("Hello kitty!");

  await helloContract.deployed();

  console.log("Deployed to address:", helloContract.address);
}

// We recommend this pattern to be able to use async/await everywhere
// and properly handle errors.
main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

6. Deploy smart contract

```
npx hardhat run scripts/deploy.js --network goerli
```

`Lưu ý` khi deploy thì ví của bạn cần có ETH đã nhé, ko sẽ ko deploy dc. Tiếp theo khi deploy thành công thì address của smart contract sẽ hiển thị ở console.log nhé

Deployed to address: 0x88cb4b51E80bCB85CA1eA23E684372E878a1EbFd //example

Xong rồi vào scan testnet để kiểm tra xem với address trã về thì đã thành công chưa nhé

![0x88cb4b51E80bCB85CA1eA23E684372E878a1EbFd](https://raw.githubusercontent.com/hanhhn/hanhhoang.dev/master/public/images/simple-smart-contract-and-dapp/5.png)

### Step 5 - Deploy smart contract lên testnet

## Coding dApp - Reactjs (step by step)
