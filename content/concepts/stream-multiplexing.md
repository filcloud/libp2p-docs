---
title: 流的多路复用 Stream Multiplexing
---

流的多路复用（一般缩写为 stream muxing）允许多个逻辑上独立的流，共用一条底层传输连接。

libp2p 应用程序一般会在通信的对端之间建立多条独立的流，甚至与一个远端同时建立多条并发的流。流的多路复用，允许我们在与一个对端交互的生命周期里，摊销建立新的[传输](/concepts/transport/)连接的额外开销。我们也只需要一次性地处理 [NAT 穿透](/concepts/nat/)，就可以建立很多条流，因为他们共用一条底层传输连接。

多路复用绝不是 libp2p 独有的。大多数通信网络都涉及某种类型的多路复用，因为传输介质通常是稀缺的，需要被许多使用者共用。例如，TCP/IP 协议栈使用唯一的端口号来区分流，从而在基础网络连接上多路复用多条 TCP 流。libp2p 的流多路复用器位于传输协议栈的“上方”，并允许多条流通过单个 TCP 端口或其他原始传输连接进行流动。

libp2p 为流多路复用器提供了一个通用的[接口](#interface)，并提供了几种[实现](#implementations)。应用程序可以启用对多个多路复用器的支持，允许在远程对端不支持某个偏好的多路复用器的情况下，自动回退到一个被广泛支持的多路复用器。

## 流多路复用在 libp2p 协议栈中的位置

libp2p 的流多路复用发生在“应用程序层”，这意味着它不是由操作系统的网络堆栈提供。但是，编写libp2p应用程序的开发人员很少需要与流多路复用器直接交互，除了在初始配置时控制启用哪些模块。

### Switch / Swarm

libp2p 在一个称为 switch（或 swarm，取决于实现）的组件中维护有关对端和已建立连接的某些状态。该 switch 提供了一个 Dial 和 Listen 接口，该接口抽象了用于给定连接的流多路复用器的实现细节。

在配置 libp2p 时，应用程序启用流复用模块，switch 将在 Dial 对端和 Listen 连接时使用它们。如果远程对端支持任何相同的流多路复用实现，则 switch 将在建立连接时选择并使用它。如果你 Dial 的对端是 switch 已经建立了连接的，则新的流将自动在现有连接上进行多路复用。

选择使用哪个流多路复用器，是在连接建立过程的早期就达成一致的。对端使用[协议协商](/concepts/protocols/#protocol-negotiation)来选择双方都支持的多路复用器，该多路复用器将“原始”传输连接升级为能够建立新流的多路复用连接。

## 接口和实现

### 接口

[流多路复用接口][interface-stream-muxing]定义了如何将流多路复用模块应用于连接以及多路复用的连接支持哪些操作。

### 实现

libp2p 中有几个可用的流多路复用模块。请注意，并非每种语言的 libp2p 的实现都支持所有的流复用器。

#### mplex

mplex 是一个专为 libp2p 开发的协议。其[协议规范](https://github.com/libp2p/specs/tree/master/mplex)定义了一个简单的多路复用协议，该协议在 libp2p 语言实现中都得到广泛支持：

- Go: [go-mplex](https://github.com/libp2p/go-mplex)
- Javascript: [js-mplex](https://github.com/libp2p/js-libp2p-mplex)
- Rust: [rust-libp2p mplex module](https://github.com/libp2p/rust-libp2p/tree/master/muxers/mplex)

#### yamux

[yamux](https://github.com/hashicorp/yamux) 是 [Hashicorp](https://www.hashicorp.com/) 设计的多路复用协议。

yamux 提供比 mplex 更复杂的流控制，并且可以在单个连接上扩展成千上万的多路复用流。

yamux 目前支持的实现：

- Go: [go-smux-yamux](https://github.com/whyrusleeping/go-smux-yamux)
- Rust: [rust-libp2p yamux module](https://github.com/libp2p/rust-libp2p/tree/master/muxers/yamux).

#### quic

[QUIC][wiki-quic] 是一种[传输](/concepts/transport/)协议，其包含一个原生的流多路复用器。libp2p 会自动使用 QUIC 传输连接的原生流多路复用器。

目前 QUIC 有 Go 语言实现的支持 [go-libp2p-quic-transport](https://github.com/libp2p/go-libp2p-quic-transport)。

#### spdy

[SPDY][wiki-spdy] 是 Google 开发的协议，它是 HTTP2 的前身。SPDY 实现了一个流多路复用器，某些 libp2p 实现支持它：

- Go: [go-smux-spdystream](https://github.com/whyrusleeping/go-smux-spdystream)
- Javascript: [js-libp2p-spdy](https://github.com/libp2p/js-libp2p-spdy)

#### muxado

[muxado](https://github.com/inconshreveable/muxado) 是一个 Go 实现的流多路复用器 [go-smux-muxado](https://github.com/whyrusleeping/go-smux-muxado)。

<!-- links -->
[interface-stream-muxing]: https://github.com/libp2p/interface-stream-muxer

[repo-multistream-select]: https://github.com/multiformats/multistream-select 

[wiki-quic]: https://en.wikipedia.org/wiki/QUIC
[wiki-spdy]: https://en.wikipedia.org/wiki/SPDY
