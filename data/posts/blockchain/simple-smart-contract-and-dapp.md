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

`Lưu y` Ai chưa có hay đã có rồi cũng nên tạo 1 Wallet mới để test nhé, tránh dùng ví chính lộ private key
Tạo wallet dễ ợt à, anh/em tự tạo nhé. Khi tạo xong nhớ switch qua testnet `Goerli`

![switch qua testnet Goerli](https://raw.githubusercontent.com/hanhhn/hanhhoang.dev/master/public/images/simple-smart-contract-and-dapp/3.png)

### Step 3 - Kiếm ETH cho test account vừa tạo

Có nhiều trang kiếm ETH cho testnet lắm. Các bạn google phát là ra. Sau đó chuyển eth cho ví test
Mình xài web https://goerlifaucet.com/ để get ETH, Login vào thì get dc nhiều ETH hơn.

![get eth](https://raw.githubusercontent.com/hanhhn/hanhhoang.dev/master/public/images/simple-smart-contract-and-dapp/4.png)

### Step 4 - Coding simple smart contract

### Step 5 - Deploy smart contract lên testnet

## Coding dApp - Reactjs (step by step)
