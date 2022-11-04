---
title: Hyperledger Fabric Introduction
date: '2022-11-04'
tags: ['BlockChain', 'Hyperledger Fabric']
draft: false
summary: 'Hyperledger Fabric is an open source enterprise-grade permissioned distributed ledger technology (DLT) platform, designed for use in enterprise contexts, that delivers some key differentiating capabilities over other popular distributed ledger or blockchain platforms.'
---

## Introduction

`Lưu ý: ` Có một số khái niệm, các bạn có thể tự google mình chỉ đi sâu vào Hyperledger Fabric

> BlockChain is an immutable transaction ledger, maintained within a distributed network of peer nodes

> Blockchain is a shared, immutable ledger that facilitates the process of recording transactions and tracking assets in a business network.

Thật ra có rất nhiều nguồn định nghĩa về blockchain, nhưng chúng ta có thể hiểu đây như là một công nghệ cho phép lưu trữ, chia sẽ, theo dỏi dữ liệu trên 1 quyển sổ cái (Ladger) trong một distributed network của các nodes ngang hàng. Những dữ liệu khi được lưu trữ trên này thì phải đảm bảo không thể thay đổi (immutable) bằng bất cứ cách nào.

`Lưu ý: ` Blockchain là công nghệ đằng sau của cryptocurrency, blockchain is NOT cryptocurrency

Blokchain 2 được chia làm 2 loại, 2 loại này giống nhau hoàn toàn về công nghệ nhưng khác nhau về permission. Tìm hiểu thêm về 2 loại blockchain này [tại đây](https://www.investopedia.com/terms/p/permissioned-blockchains.asp)

- Permissioned blockchain (Private blockchain): Giới hạn truy cập, cần phải identity và có permission
- Permissionless blockchain (Public blockchain): Truy cập tự do chỉ cần 1 địa chỉ ví

Những network bạn thấy hiện nay như bitcoin, ethereum, BNB chain đều là _Permissionless blockchain_. Những chain này dc public và có sự đóng góp đáng kể bởi cộng đồng. Còn _Permissioned blockchain_ phù hợp với doanh nghiệp các tổ chức tài chính vì cần phải identity và has permission mới có thể truy cập

Để sử dụng 1 mạng lưới blockchain cho danh nghiệp, chúng ta cần consider tới một số yếu tố sau:

- Participants must be identified/identifiable
- Networks need to be permissioned
- High transaction throughput performance
- Low latency of transaction confirmation
- Privacy and confidentiality of transactions and data pertaining to business transactions

Vì là doanh nghiệp nên những thông tin, tốc độ, định danh, quyền riêng tư, bảo mật là những thứ rất quan trọng.

Trong phần đầu tiên, chúng ta cùng tìm hiểu **Hyperledger Fabric**. Hyperledger Fabric là gì? tại sao cách doanh nghiệp cần nó.

## Hyperledger Fabric (HLF)

> Hyperledger Fabric is an open source enterprise-grade permissioned distributed ledger technology (DLT) platform, designed for use in enterprise contexts, that delivers some key differentiating capabilities over other popular distributed ledger or blockchain platforms.

**Hyperledger Fabric** là một open source về blockchain được thiết để sử dụng cho doanh nghiệp, **Hyperledger Fabric** là Permissioned blockchain, có một số lưu ý quan trọng sau

- Distributed ledger technology (DLT) platform
- Was established under the Linux Foundation
- Has a highly modular and configurable architecture
- Support smart contracts authored in general-purpose programming languages such as Java, Go and Node.js
- **Important thing:** support for pluggable consensus protocols that enable the platform to be more effectively customized to fit particular use cases and trust models.
- **do not require a native cryptocurrency** to incent costly mining or to fuel smart contract execution
- Is better performing platforms available today both in terms of transaction processing and transaction confirmation latency
- Privacy and confidentiality

## Modularity

**Hyperledger Fabric** được thiết kế theo hướng module, ngày cả giao thức đồng thuận cũng dc xem như là một module và có thể dễ dàng dc gắn vào

Có một thủa thuận rằng "no one blockchain to rule them all", có nghĩa là khộng có blockchain nào để cai trị tất cả. HLF có thể dc cấu hình theo nhiều cách để đáp ứng các thu cầu và giải pháp đa dạng cho nhiều trường hợp sử dụng trong nhiều trường hợp

## Permissioned vs Permissionless Blockchains

Xem thêm [tại đây](https://www.investopedia.com/terms/p/permissioned-blockchains.asp)

## Smart Contracts

Xem thêm [tại đây](https://ethereum.org/en/smart-contracts/)

## A New Approach

> Fabric introduces a new architecture for transactions that we call execute-order-validate. It addresses the resiliency, flexibility, scalability, performance and confidentiality challenges faced by the order-execute model by separating the transaction flow into three steps:

Fabric giới thiệu 1 kiến trúc mới cho những transactions. Fabric gọi đó là **execute-order-validate**. Kiến trúc giúp giải quyết các thách thức của blockchain bao gồm phục hồi (resiliency), linh hoạt (flexibility), mở rộng (scalability), hiệu năng (performance), bảo mật (confidentiality) bằng cách tách transaction floow thành 3 bước:

- Thực thi 1 transaction và kiểm tra tính đúng đắn của nó,
- Chạy có thứ tự transactions thông qua giao thức đồng thuận
- Validate transaction dựa trên chính sách của từng ứng dụng trước khi commit to ladger

Thiết kế này hoàn toàn khác với mô hình order-execute, theo đó Fabric thực thi transactions trước khi đạt được sự đồng thuận cuối cùng

## Privacy and Confidentiality

Hyperledger Fabric, being a permissioned platform, enables confidentiality through its channel architecture and private data feature. In channels, participants on a Fabric network establish a sub-network where every member has visibility to a particular set of transactions. Thus, only those nodes that participate in a channel have access to the smart contract (chaincode) and data transacted, preserving the privacy and confidentiality of both. Private data allows collections between members on a channel, allowing much of the same protection as channels without the maintenance overhead of creating and maintaining a separate channel.

## Pluggable Consensus

- CFT (crash fault-tolerant)
- BFT (byzantine fault-tolerant).

## Performance and Scalability

> Several research papers have been published studying and testing the performance capabilities of Hyperledger Fabric. The latest [scaled Fabric to 20,000 transactions per second](https://arxiv.org/abs/1901.00910)

## Conclusion

Chốt lại là **Hyperledger Fabric** có tất cả các yêu cầu mà một ngữ cảnh doanh nghiệp cần đến chi tiết sẽ đi sâu ở những phần sau, nhất là những mục ở phần _Introduction_ đã bỏ qua vì toàn lý thuyết

- Privacy and Confidentiality
- Pluggable Consensus
- Performance and Scalability
