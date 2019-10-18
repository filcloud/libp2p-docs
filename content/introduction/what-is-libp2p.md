---
title: "What is libp2p?"
weight: 2
---

Good question! The one-liner pitch is that libp2p is a modular system of *protocols*, *specifications* and *libraries* that enable the development of peer-to-peer network applications.

好问题！ 简单的说法是 libp2p 是由协议，规范和库组成的模块化系统，可用于开发对端网络应用程序。

<!--more-->

## Peer-to-peer basics

There's a lot to unpack in that one-liner! Let's start with the last bit, "peer-to-peer network applications." You may be here because you're knee-deep in development of a peer-to-peer system and are looking for help. Likewise, you may be here because you're just exploring the world of peer-to-peer networking for the first time. Either way, we ought to spend a minute defining our terms upfront, so we can have some [shared vocabulary][glossary] to build on.

A [peer-to-peer network][definition_p2p] is one in which the participants (referred to as [peers][definition_peer] or nodes) communicate with one another directly, on more or less "equal footing". This does not necessarily mean that all peers are identical; some may have different roles in the overall network. However, one of the defining characteristics of a peer-to-peer network is that they do not require a priviliged set of "servers" which behave completely differently from their "clients", as is the case in the the predominant [client / server model][definition_client_server].

Because the definition of peer-to-peer networking is quite broad, many different kinds of systems have been built that all fall under the umbrella of "peer-to-peer". The most culturally prominent examples are likely the file sharing networks like bittorrent, and, more recently, the proliferation of blockchain networks that communicate in a peer-to-peer fashion.

## 对端基础

有很多东西要解释！让我们从最基础的开始，“对端网络应用程序”。您之所以在这里，可能是因为您对对端系统的开发非常热衷，并且正在寻求帮助。同样，您之所以在这里，是因为您只是第一次探索对端网络的世界。无论哪种情况，我们都应该花一点时间预先定义我们的术语，以便我们可以建立一些 [共享词汇] [glossary]。

[对端网络] [definition_p2p] 是参与者（称为[peers] [definition_peer]或节点）彼此或多或少地在“平等基础”上进行通信的网络。这并不一定意味着所有节点都是相同的，有些可能在整个网络中扮演不同的角色。然而，对端网络的定义特征之一是，它们不需要专有的“服务器”集，其行为与对应的“客户端”完全不同，比如流行的 [客户端/服务器模型] [definition_client_server]。

因为对端网络的定义非常广泛，所以基于“对端”框架已经建立了许多不同种类的系统。最传统的例子可能是文件共享网络，例如 bittorrent，最近，以对端方式通信的区块链网络开始流行。

## What problems can libp2p solve?

While peer-to-peer networks have many advantages over the client / server model, there are also challenges that are unique and require careful thought and practice to overcome. In our process of overcoming these challenges while building [IPFS](https://ipfs.io), we took care to build our solutions in a modular, composable way, into what is now libp2p. Although libp2p grew out of IPFS, it does not require or depend on IPFS, and today [many projects][built_with_libp2p] use libp2p as their network transport layer. Together we can leverage our collective experience and solve these foundational problems in a way that benefits an entire ecosystem of developers and a world of users.



Here I'll try to briefly outline the main problem areas that are addressed by libp2p today (early 2019). This is an ever-growing space, so don't be surprised if things change over time. We'll do our best to keep this section up-to-date as things progress, but if you notice something missing or have other ideas for improving this documentation, please [reach out to let us know][help_improve_docs].

<!-- TODO: as concept articles are written expanding on the below, add links -->

## libp2p 解决的问题

尽管对端网络相对于客户端/服务器模型具有许多优势，但也存在一些独特的挑战，需要认真思考和实践才能克服。在构建 [IPFS](https://ipfs.io) 的过程中克服了的这些挑战，我们谨慎地以模块化，可组合的方式将解决方案构建到现在的 libp2p 中。尽管 libp2p 脱离了 IPFS，但是它并不需要 IPFS或不依赖 IPFS，如今，[许多项目] [built_with_libp2p] 使用 libp2p 作为其网络传输层。我们可以共同利用我们解决这些基本问题的集体经验，以使整个开发人员生态系统和用户世界受益。

在这里，我将尝试简要概述今天（2019年初） libp2p 解决的主要问题。这是一个不断变化的部分，所以如果方案随着时间的推移而变化，请不要感到惊讶。我们会尽力使本节保持最新状态，但是，如果您发现缺少内容或对改进本文档有其他想法，请 [联系我们] [help_improve_docs]。

### Transport

At the foundation of libp2p is the transport layer, which is responsible for the actual transmission and receipt of data from one peer to another. There are many ways to send data across networks in use today, with more in development and still more yet to be designed. libp2p provides a simple [interface](https://github.com/libp2p/interface-transport) that can be adapted to support existing and future protocols, allowing libp2p applications to operate in many different runtime and networking environments.

### 传输

libp2p 的基础是传输层，它负责从一个对等方到另一个对等方的实际数据传输和接收。 如今，有许多方法可以通过网络发送数据，还有更多的方法正在开发中，还有更多尚待设计。 libp2p 提供了一个简单的 [接口](https://github.com/libp2p/interface-transport)，可以对其进行调整以支持现有和将来的协议，从而使 libp2p 应用程序可以在许多不同的运行时和联网环境中运行。

### Identity

In a world with billions of networked devices, knowing who you're talking to is key to secure and reliable communication. libp2p uses [public key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography) as the basis of peer identity, which serves two complementary purposes.  First, it gives each peer a globally unique "name", in the form of a [PeerId][definition_peerid]. Second, the `PeerId` allows anyone to retrieve the public key for the identified peer, which enables secure communication between peers.

### 身份识别

在拥有数十亿个联网设备的世界中，知道与您交谈的人是确保安全可靠是通信的关键。 libp2p 使用[公钥加密](https://en.wikipedia.org/wiki/Public-key_cryptography) 作为对等身份的基础，这具有两个互补的目的。 首先，它以 [PeerId] [definition_peerid] 的形式为每个对等方提供全局唯一的“名称”。其次，“ PeerId”允许任何人检索所标识对等方的公钥，从而实现对等方之间的安全通信。

### Security

It's essential that we are able to send and receive data between peers *securely*, meaning that we can trust the [identity](#identity) of the peer we're communicating with and that no third-party can read our conversation or alter it in-flight.

libp2p supports "upgrading" a connection provided by a [transport](#transport) into a securely encrypted channel. The process is flexible, and can support multiple methods of encrypting communication. The current default is [secio][definition_secio], with support for [TLS 1.3](https://www.ietf.org/blog/tls13/) under development.

### 安全

我们必须能够*安全地*在对等方之间发送和接收数据，这意味着我们可以信任与之通信的对等方的 [身份](#identity)，并且任何第三方都不能读取我们的对话或进行在线篡改。

libp2p 支持将 [传输](#transport) 提供的连接“升级”到安全加密的通道中。 该过程很灵活，可以支持多种加密通信方式。当前默认方式为 [secio] [definition_secio]，[TLS 1.3](https://www.ietf.org/blog/tls13/) 的支持正在开发中。

### Peer Routing

When you want to send a message to another peer, you need two key pieces of information: their [PeerId][definition_peerid], and a way to locate them on the network to open a connection.

There are many cases where we only have the `PeerId` for the peer we want to contact, and we need a way to discover their network address. Peer routing is the process of discovering peer addresses by leveraging the knowledge of other peers.

In a peer routing system, a peer can either give us the address we need if they have it, or else send our inquiry to another peer who's more likely to have the answer. As we contact more and more peers, we not only increase our chances of finding the peer we're looking for, we build a more complete view of the network in our own routing tables, which enables us to answer routing queries from others.

The current stable implementation of peer routing in libp2p uses a [distributed hash table][definition_dht] to iteratively route requests closer to the desired `PeerId` using the [Kademlia][wiki_kademlia] routing algorithm.

### 节点路由

当您想向另一个对等方发送消息时，您需要两个关键信息：它们的 [PeerId] [definition_peerid]，以及为了建立连接而在网络上定位它们的方法。

在许多情况下，我们仅需要要联系的节点的“ PeerId ”，因此我们需要一种发现其网络地址的方法。节点路由是通过利用其他节点的路由表来发现其它节点地址的过程。

在节点路由系统中，一个节点可以给我们我们需要的地址（如果有），也可以将查询发送给另一个更有可能得到答案的节点。随着我们与越来越多的节点建立连接，我们不仅提高了寻找所需节点的机会，而且还在自己的路由表中建立了网络的更完整视图，这使我们能够回答来自其它节点的路由查询。

libp2p 中节点路由的当前稳定实现使用 [分布式哈希表][definition_dht] 和 [Kademlia][wiki_kademlia]路由算法将请求迭代地路由至更接近所需的“ PeerId”。

### Content Discovery

In some systems, we care less about who we're speaking with than we do about what they can offer us. For example, we may want some specific piece of data, but we don't care who we get it from since we're able to verify its integrity.

libp2p provides a [content routing interface][interface_content_routing] for this purpose, with the primary stable implementation using the same [Kademlia][wiki_kademlia]-based DHT as used in peer routing.

### 

### Messaging / PubSub

Sending messages to other peers is at the heart of most peer-to-peer systems, and pubsub (short for publish / subscribe) is a very useful pattern for sending a message to groups of interested receivers.

libp2p defines a [pubsub interface][interface_pubsub] for sending messages to all peers subscribed to a given "topic". The interface currently has two stable implementations; `floodsub` uses a very simple but inefficient  "network flooding" strategy, and [gossipsub](https://github.com/libp2p/specs/tree/master/pubsub/gossipsub) defines an extensible gossip protocol.  There is also active development in progress on [episub](https://github.com/libp2p/specs/blob/master/pubsub/gossipsub/episub.md), an extended `gossipsub` that is optimized for single source multicast and scenarios with a few fixed sources broadcasting to a large number of clients in a topic.

[glossary]: {{< ref "/reference/glossary.md" >}}
[definition_dht]: {{< ref "/reference/glossary.md#dht" >}}
[definition_p2p]: {{< ref "/reference/glossary.md#p2p" >}}
[definition_peer]: {{< ref "/reference/glossary.md#peer" >}}
[definition_peerid]: {{< ref "/reference/glossary.md#peerid" >}}
[definition_secio]: {{< ref "/reference/glossary.md#secio" >}}
[definition_muiltiaddress]: {{< ref "/reference/glossary.md#multiaddr" >}}
[definition_client_server]: {{< ref "/reference/glossary.md#client-server" >}}

[interface_content_routing]: https://github.com/libp2p/interface-content-routing
[interface_pubsub]: https://github.com/libp2p/specs/tree/master/pubsub


[built_with_libp2p]: /TODO
[help_improve_docs]: /TODO

[wiki_kademlia]: https://en.wikipedia.org/wiki/Kademlia
