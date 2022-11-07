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

![The sample network](https://hyperledger-fabric.readthedocs.io/en/latest/_images/network.diagram.1.png)

Có 3 tổ chức R0, R1, R2 quyết định khởi chạy 1 network. Nextwork này có cấu hình là CC1. Những definition, policies, roles của mỗi tổ chức đều dc định nghĩa, xác định trên channel

Trên channel C1, 2 tổ chức R1 R2 tham gia ngang hàng có tên là P1 P2. Trong khi R0 sỡ hữu O, O là the ordering service of channel. Tất những node đều sẽ có 1 bản copy legder (L1) của channel, L1 là nơi transactions được recorded. Lưu ý rằng bản copy của ledger giữ bởi The ordering service và nó ko bao gồm state database. R1 R2 cũng sẽ tương tác với channel thông qua ứng dụng A1 A2 mà chúng sở hữu. Cả 3 tổ chức này có Certificate Authority những chứng chỉ này đã được tạo ra là cách chứng chỉ cần thiết cho các nodes, admins, organizations definitions, and applications mà chúng sở hữu

## Creating the network

![Creating the network](https://hyperledger-fabric.readthedocs.io/en/latest/_images/network.diagram.2.png)

Bước đầu tiên để tạo 1 network or 1 channel là agree và sau đó define cấu hình của nó.

The channel configuration CC1 đã dc đồng ý bởi organizations R1, R2 và RO và được bao gồm trong 1 block được biết như là “configuration block” nó thường được tạo bở `configtxgen` tool từ 1 file yaml `configtx.yaml`. Mặc dù những channel này có khả năng tạo bởi 1 organization và sau đó mời những organizations khác (tìm hiểu sau - mình cũng chưa hiểu lắm)

Khi một configuration block tồn tại, một channel có thể cho là **tồn tại 1 cách hợp lý (logically exist)**, mặc dù không components được tham gia vào nó (về mặt physically). Cái configuration block này chứa 1 bản ghi của những organizations có thể join components và tương tác với channel, như là những chính sách nó define structure for chách quyết định đưa ra như thế nào vào kết quả cụ thể đạt dc.

Định danh của admin phải dc tạo bởi Certificate Authority (CA) có liên kết với mỗi tổ chức. Organizations R1, R2, and R0 have had their certifications and organization definition created by CA1, CA2, and CA0, respectively. For information about how to create a CA, check out Planning for a CA. After the CA has been created, check out Registering and enrolling identities with a CA for information about how to define an organization and create identities for admins and nodes.

### Certificate Authorities

- Certificate Authorities play a key role in the network because they dispense X.509 certificates
- Certificates issued by CAs can also be used to sign transactions to indicate that an organization endorses the transaction result

## Join nodes to the channel

## Install, approve, and commit a chaincode

## Using an application on the channel

## Joining components to multiple channels

### Creating the new channel configuration

### Add components to the new channel

## Adding an organization to an existing channel

## Network recap
