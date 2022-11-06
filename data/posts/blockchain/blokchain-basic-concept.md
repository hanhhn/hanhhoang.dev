---
title: Blockchain Basic Concept
date: '2022-11-05'
tags: ['BlockChain', 'Hyperledger Fabric']
draft: false
summary: 'At the heart of a blockchain network is a distributed ledger that records all the transactions that take place on the network.'
---

## What is a Blockchain?

### A Distributed Ledger

Trái tim của mạng lưới blockchain chính là một quyển sổ cái phân tán (distributed ladger), ghi nhận lại tất cả giao dịch diển ra trên đó

Một blockchain ladger thường được mô tả là **decentralized** bởi vì nó replicated giữa nhiều node tham gia vào mạng lưới. Mỗi node đều collaborate & maintenance

![A Distributed Ledger](https://hyperledger-fabric.readthedocs.io/en/latest/_images/basic_network.png)

Ngoài decentralized và collaborative, thông tin được lưu trữ trên blockchain chỉ dc append thêm, sử dung các thuật toán mã hoá để đảm bảo răng giao dịch được thêm vào quyển sổ cái là không thể bị thay đổi (immutability)

### Smart Contracts

Đễ hỗ trợ cập nhật thông tin toàn vẹn và cho phép toàn bộ ledger functions (transacting, querying, etc). Blockchain network sử dụng smart contract để chung cấp quyền truy cập đến ledger

Nói nôm na smart contract là 1 chương trình con chứa tập các lệnh chạy trên blockchain network cho phép truy cập vào ladger.

![Smart Contracts](https://hyperledger-fabric.readthedocs.io/en/latest/_images/Smart_Contract.png)

Smart contract không chỉ là một cơ chế chính cho phép đóng gói thông tin và giữ cho thông tin đơn giản trện network

### Consensus

Consensus hay còn gọi là consensus protocol. Consensus là giao thức đồng thuận được thực thi khi có 1 transaction làm thay đổi state trên mạng lưới

Để chắc chắn rằng transaction làm thay đổi state sẽ dc update vào ladger khi được approved bới tất cả các node tham gia vào mạng lưới

![Consensus](https://hyperledger-fabric.readthedocs.io/en/latest/_images/consensus.png)

Nói toẹt ra giao thức đồng luận giữ cho data ở trên blockchain an toàn, bất cứ thay đổi nào ảnh hưởng tới state của hệ thống (sinh ra transaction ảnh hưởng tới dữ liệu) đều phải được approved bởi các node ngang hàng (hay còn gọi là validator)

## Why is a Blockchain useful?

### Today’s Systems of Record

=))

### The Blockchain Difference

![The Blockchain Difference](https://hyperledger-fabric.readthedocs.io/en/latest/_images/future_net.png)

Blockchain network là nơi mà mọi node ngang hàngg khi tham gia vào để có 1 bản replicated copy của ledger. Ngoài ra thông tin của ledger dc chia sẻ, các process update ledger cũng dc chia sẽ. Không giống như hệ thống ngày nay. Nơ và người tham gia vào hệ thông riêng được sử dụng prvivate thông tin.

## What is Hyperledger Fabric?

- The Linux Foundation founded the Hyperledger project in 2015
- Khuyến khích đóng góp từ cộng đồng
- _Hyperledger Fabric_ là một dự án blockchain trong Hyperledger, có đầy đủ các đặc điểm của 1 blockchain khác
- _Hyperledger Fabric_ is private & permissioned
- the members of a Hyperledger Fabric network enroll through a trusted Membership Service Provider (MSP)
- _Hyperledger Fabric_ xây dựng theo hướng pluggable. Data có thể lưu trữ với nhiều format, cơ chế đồng thuận có thể swapped, MSP muiliple support
- _Hyperledger Fabric_ cung cấp khá năng tạo các channels, cho phép các node tham gia tạo một ledger riệng của transactions

### Shared Ledger

_Hyperledger Fabric_ có một hệ thống sổ cái con gồm 2 thành phần: world state & transaction log. Mỗi thành phần tham gia có một bản copy của ledger

The world state component mô tả state của leger tại một thời điểm nhất định. Nó là database của leger. The transaction log component record tất cả những transaction là kết quả hiện tại của the world state. Nó là the update history of the world state.

_The ledger is a combination of the world state database and the transaction log history._

### Smart Contracts

_Hyperledger Fabric smart contracts_ được viết bằng **chaincode** và được gọi bởi ứng dụng bên ngoài của blockchain khi ứng dụng cần tương tác với legeder (sinh ra transaction). Trong nhiều trường hợp, chiancode tương tác chỉ với the database component of the ledger, The world state, không có the transcation log

Chaincoide có thể dc implemented bởi 1 vài ngôn ngữ lập trình. Hiện tại là go, nodejs, java được support

### Privacy

Tuỳ thuộc vào nhu cầu của từng network, nhưng thành phần tham gia vào Business-to-Business (B2B) network có thể cực kỳ nhạy cảm về thông tin mà nó chia sẽ. Nhưng những networks khác Privacy sẽ không phải là ưu tiên hàng đầu

_Privacy_ là key trong Hyperledger Fabric

### Consensus

Tìm hiểu chi tiết sau, phần này khó

## Reference

[https://hyperledger-fabric.readthedocs.io/en/latest/blockchain.html](https://hyperledger-fabric.readthedocs.io/en/latest/blockchain.html)
