---
title: Hyperledger Fabric Model
date: '2022-11-06'
tags: ['BlockChain', 'Hyperledger Fabric']
draft: false
summary: 'This section outlines the key design features woven into Hyperledger Fabric that fulfill its promise of a comprehensive, yet customizable, enterprise blockchain solution'
---

## Hyperledger Fabric Model

Trong post này chúng ta sẽ nói về những thành phấn chính để tạo nên **Hyperledger Fabric**

### Assets

> Assets — Asset definitions enable the exchange of almost anything with monetary value over the network, from whole foods to antique cars to currency futures.

Assets được định nghĩa cho phép trao đổi hầu như toàn bộ những thứ có giá trị trên network. Assets có thể bao gồm những thứ hữu hình đến những thứ vô hình. _Hyperledger Fabric_ cung cấp khả năng chỉnh sửa assets sử dụng chaincode transaction

Asset được đại diện trong Hyperledger Fabric như là 1 collection của cặp key-value, với state thay đổi được ghi như là transactions trên 1 channel ledger. Assets có thể dc đại diện bởi binary or json

### Chaincode

> Chaincode — Chaincode execution is partitioned from transaction ordering, limiting the required levels of trust and verification across node types, and optimizing network scalability and performance.

Chaincode is phần mềm định nghĩa 1 or nhiều tài sản, và là transaction instructions cho chỉnh sửa assets. Nói cách khác, chaincode là business logic. Chaincode thuân theo rule đọc or thay đổi key-value pairs or những state khác của database. Chiancode functions thực thi dựa trên state database hiện tại của ledger và được khỏi tạo thông qua một số transaction được xuất. Chiancode execution results trong tập key-value pairs có thể submited đến network và applied đến ledger on tất các node ngang hàng

### Ledger Features

> Ledger Features — The immutable, shared ledger encodes the entire transaction history for each channel, and includes SQL-like query capability for efficient auditing and dispute resolution.

Ledger là bản ghi tuần tựm, chống giả mạo của tất cả state transitions trong fabric. State transitions là một kết quả của chaincode invocations (‘transactions’) được submitted bởi các thành phần tham gia vào mạng lưới. Mỗi transaction result trong tập key-value pairs được committed đến leger như là creates, updates, deletes

Ledger là bao gồm 1 blockchain (chain) để lưu trữ không thể thay đổi, lưu tuần tự trong blocks, cũng như 1 state database để duy trì current state of fabric. Có mỗi ledger cho mỗi channel. Mỗ peer (node) có 1 bản copy của ledger cho mỗi channel mà nó là thành viện

_Some features of a Fabric ledger:_

- Query and update ledger using key-based lookups, range queries, and composite key queries
- Read-only queries using a rich query language (if using CouchDB as state database)
- Read-only history queries — Query ledger history for a key, enabling data provenance scenarios
- Transactions consist of the versions of keys/values that were read in chaincode (read set) and keys/values that were written in chaincode (write set)
- Transactions contain signatures of every endorsing peer and are submitted to ordering service
- Transactions are ordered into blocks and are “delivered” from an ordering service to peers on a channel
- Peers validate transactions against endorsement policies and enforce the policies
- Prior to appending a block, a versioning check is performed to ensure that states for assets that were read have not changed since chaincode execution time
- There is immutability once a transaction is validated and committed
- A channel’s ledger contains a configuration block defining policies, access control lists, and other pertinent information
- Channels contain Membership Service Provider instances allowing for crypto materials to be derived from different certificate authorities

`Lưu ý:` có một vài câu ko dịch sang tiếng việt dc vì dịch sang rất khó hiểu, cũng chả biết dịch sao

### Privacy

> Privacy — Channels and private data collections enable private and confidential multi-lateral transactions that are usually required by competing businesses and regulated industries that exchange assets on a common network.

### Security & Membership Services

> Security & Membership Services — Permissioned membership provides a trusted blockchain network, where participants know that all transactions can be detected and traced by authorized regulators and auditors.

### Consensus

> Consensus — A unique approach to consensus enables the flexibility and scalability needed for the enterprise.

## Reference

[https://hyperledger-fabric.readthedocs.io/en/latest/fabric_model.html](https://hyperledger-fabric.readthedocs.io/en/latest/fabric_model.html)
