---
title: Introduction
date: '2022-11-04'
tags: ['BlockChain', 'Hyperledger Fabric']
draft: false
summary: 'Hyperledger Fabric is an open source enterprise-grade permissioned distributed ledger technology (DLT) platform, designed for use in enterprise contexts, that delivers some key differentiating capabilities over other popular distributed ledger or blockchain platforms.'
---

## Introduction

> BlockChain is an immutable transaction ledger, maintained within a distributed network of peer nodes

> Blockchain is a shared, immutable ledger that facilitates the process of recording transactions and tracking assets in a business network.

Thật ra có rất nhiều nguồn định nghĩa về blockchain, nhưng chúng ta có thể hiểu đây như là một công nghệ cho phép lưu trữ, chia sẽ, theo dỏi dữ liệu trên 1 quyển sổ cái (Ladger) trong một distributed network của các nodes ngang hàng. Những dữ liệu khi được lưu trữ trên này thì phải đảm bảo không thể thay đổi (immutable) bằng bất cứ cách nào.

`Lưu ý: ` Blockchain là công nghệ đằng sau của cryptocurrency, blockchain is NOT cryptocurrency

Blokchain 2 được chia làm 2 loại, 2 loại này giống nhau hoàn toàn về công nghệ nhưng khác nhau về permission. Tìm hiểu thêm về 2 loại blockchain này [tại đây](https://www.investopedia.com/terms/p/permissioned-blockchains.asp)

- Permissioned blockchain (Private blockchain): Giới hạn truy cập, cần phải identity và có permission
- Permissionless blockchain (Public blockchain): Truy cập tự do chỉ cần 1 địa chỉ ví

Những network bạn thấy hiện nay như bitcoin, ethereum, BNB chain đều là *Permissionless blockchain*. Những chain này dc public và có sự đóng góp đáng kể bởi cộng đồng. Còn *Permissioned blockchain* phù hợp với doanh nghiệp các tổ chức tài chính vì cần phải identity và has permission mới có thể truy cập

Trong phần đầu tiên, chúng ta cùng tìm hiểu **Hyperledger Fabric**. Hyperledger Fabric là gì? tại sao cách doanh nghiệp cần nó.

Để sử dụng 1 mạng lưới blockchain cho danh nghiệp, chúng ta cần consider tới một số yếu tố sau:

- Participants must be identified/identifiable
- Networks need to be permissioned
- High transaction throughput performance
- Low latency of transaction confirmation
- Privacy and confidentiality of transactions and data pertaining to business transactions

## Hyperledger Fabric

## Modularity