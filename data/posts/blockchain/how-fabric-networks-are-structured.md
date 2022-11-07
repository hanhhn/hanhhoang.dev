---
title: How Fabric networks are structured
date: '2022-11-07'
tags: ['BlockChain', 'Hyperledger Fabric']
draft: false
summary: 'This topic will describe, at a conceptual level, how Hyperledger Fabric allows organizations to collaborate in the formation of blockchain networks'
---

Trong topic này sẽ mô tả ở mức **khái niệm**, Làm thế nào _Hyperledger Fabric_ cho phép các tổ chức cộng tác trong hình thành blockchain network. Nếu bạn là architect, administrator or developer, bạn có thể sử dụng topic này để có sự hiển biết vững chắc của cấu trúc chính và thực thi các thành phần trong Hyperledger Fabric blockchain network. Trong topic này sẽ sử dụng ví dụ có thể quản lý để giới thiệu tất cả component chính trong blockchain network

Sau khi đọc topic and hiểu về concept of poilicies, bạn có thể có hiểu biết vững chắc về quyết định mà cách tổ chức cần đưa ra để thiết lập các chính sách. Bạn cũng sẽ hiểu biết làm thế nào để những tổ chức quản lý sự phát triển network

Note: in this topic, we’ll refer to the structure of a network that does not have a “system channel”, a channel run by the ordering service that ordering nodes are bootstrapped with. For a version of this topic that does use the system channel, check out Blockchain network.

## What is a blockchain network?

Blockchain network là một công nghệ nền tảng chung cấp cho ledger và smart contract (which are packaged as part of a "chaincode") phục vụ cho applications. Smart contract được dùng để tạo ra transaction. chúng được phân phối cho mọi node than gia vào network và được immutably recorded. Users của ứng dụng có thể là end user sử dụng client application or blockchain network administrators

Trong hầu hết các trường hợp, nhiều tổ chức kết hợp cùng nhau để tạo thành 1 channel nơi mà những transactions được gọi on chaincodes và nơi mà permissions được xác định bởi tập các policies nó đồng ý để khi những channel được cấu hình ban đầu. Hơn thế, những chính sách có thể thay đổi theo thời gian tuỳ theo thoã thuận của cách tổ chức

Trong topic này, chúng ta sẽ tham khảo cả **network** & **channel**.

## The sample network

## Creating the network

### Certificate Authorities

## Join nodes to the channel

## Install, approve, and commit a chaincode

## Using an application on the channel

## Joining components to multiple channels

### Creating the new channel configuration

### Add components to the new channel

## Adding an organization to an existing channel

## Network recap
