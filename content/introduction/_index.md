---
title: Introduction
weight: 1
pre: '<i class="fas fa-fw fa-comments"></i> '
---

Welcome to the libp2p documentation portal! Whether you’re just learning how to build peer-to-peer systems with libp2p, want to dive into peer-to-peer concepts and solutions, or are looking for detailed reference information, this is the place to start.

欢迎来到 libp2p 文档入门！无论你仅仅使用 libp2p 构建对端系统，想要深入研究对端概念和解决方案，或是寻求详细参考信息，都可以从这里开始。

## Overview

Head over to [What is libp2p?](/introduction/what-is-libp2p/) for an introduction to the basics of libp2p and an overview of the problems it addresses.

## 概述

查看 [什么是 libp2p?](/introduction/what-is-libp2p/) 获得 libp2p 的基础知识和其解决问题的概述。

## Tutorials

If you want to dive in, check out our collection of [tutorials](/tutorials/), which will help guide you through your explorations of libp2p.

## 教程

如果你想深入研究， 请查看我们的 [教程](/ tutorials /)，这将有助于指导您完成对 libp2p 的探索。

## Examples

If you want to get a feel for what's possible with libp2p, or just want to see some idiomatic usage, check out the [examples](/examples/). Each libp2p implementation maintains a set of working example projects that can illustrate key concepts and use cases.

## 示例

如果您想了解 libp2p 的功能，或者只是想了解一些惯用用法，请查看[示例](/ examples /)。 每个 libp2p 实现都维护一组可运行的示例项目，这些示例项目可以演示关键概念和用例。

## Reference

## 参考

### Specifications & Planning

While libp2p has several implementations, it is fundamentally a set of protocols for peer identity, discover, routing, transport and more.

See the [specifications section](/reference/specs/) for details.

### 规范和计划

尽管 libp2p 具有多种实现，但从根本上讲，它是一组用于对等身份认证，发现，路由，传输等的协议。

有关详细信息，请参见 [规范部分](/reference/specs /)。

### Implementations

At the core of libp2p is a set of [specifications](/reference/specs/), which together form the definition for what libp2p is in the abstract and what makes a "correct" libp2p implementation. Today, implementations of libp2p exist in several languages, with varying degrees of completeness. The most complete implementations are in [Go](/reference/go/) and [JavaScript](/reference/js/), with [rust](https://github.com/libp2p/rust-libp2p) maturing rapidly.

In addition to the implementations above, the libp2p community is actively working on implementations in [python](https://github.com/libp2p/py-libp2p) and [the JVM via Kotlin](https://github.com/web3j/libp2p). Please check the project pages for each implementation to see its status and current state of completeness.

### 实现

libp2p 的核心是一组 [规范](/reference/specs/)，它们定义了 libp2p 的抽象概念以及正确实现。 如今，libp2p 已经以多种语言实现，并且具有不同程度的完整性。最完整的实现是 [Go](/reference/go/) 和 [JavaScript](/reference/js/)，其中 [rust](https://github.com/libp2p/rust-libp2p) 迅速发展。

除了上述实现之外，libp2p 社区还积极实现 [python](https://github.com/libp2p/py-libp2p) 和 [Kotlin 实现的 JVM](https://github.com/web3j/libp2p)。请检查每个实现的项目页面，以查看其状态和当前的完整性状态。

## Community

Get in touch with other members of the libp2p community who are building tools and applications with libp2p! You can ask questions, discuss new ideas, or get support for problems at https://discuss.ipfs.io, but you can also [hop on IRC](/community/irc/) for a quick chat.

See the other links in the community section for more information about meetings, events, apps people are building, and more.

Information about contributing to libp2p and about other software projects in the community are also hosted here.

## 社区

获取与 libp2p 社区中正在使用 libp2p 构建工具和应用程序的其他成员的联系！您可以在 https://discuss.ipfs.io 上提问，讨论新想法或获得问题的支持，但也可以 [加入IRC](/community/irc/) 进行快速聊天。

请参阅社区部分中的其他链接，以获取有关会议，事件，人们正在构建的应用程序等的更多信息。

这里还托管了有关为 libp2p 做出贡献以及社区中其他软件项目的信息。

### Get Involved

libp2p is an open-source community project. While [Protocol Labs](https://protocol.ai) is able to sponsor some of the work around it, much of the design, code, and effort is contributed by volunteers and community members like you. If you’re interested in helping improve libp2p, check the [contributing](/contributing/) guide to get started.

If you are diving in to contribute new code, make sure you check both the [contribution guidelines](https://github.com/libp2p/community/blob/master/CONTRIBUTE.md) and the style guide for your language ([Go](https://github.com/ipfs/community/blob/master/CONTRIBUTING_GO.md), [JavaScript](https://github.com/ipfs/community/blob/master/CONTRIBUTING_JS.md)).

### 参与其中

libp2p 是一个开源社区项目。 尽管 [协议实验室](https://protocol.ai) 可以赞助围绕它的一些工作，但是许多设计，代码和成就都是由志愿者和像您这样的社区成员做出的。 如果您有兴趣帮助改进 libp2p，请查看 [贡献](/contributing/) 指南以开始。

如果您想贡献新代码，请确保同时检查 [贡献准则](https://github.com/libp2p/community/blob/master/CONTRIBUTE.md) 和编码风格指南([ Go](https://github.com/ipfs/community/blob/master/CONTRIBUTING_GO.md), [JavaScript](https://github.com/ipfs/community/blob/master/CONTRIBUTING_JS.md)。

### Related Projects

libp2p began as part of the [IPFS](https://ipfs.io) project, and is still an essential component of IPFS. As such, libp2p composes well with the abstractions and tools provided by other projects in the IPFS "family". Check their individual sites for specific information and references:

- [IPFS](https://libp2p.io) is the InterPlanetary File System, which uses libp2p as its networking layer.
- [Multiformats](https://multiformats.io) is a variety of *self-describing* data formats.
- [IPLD](https://ipld.io) is a set of tools for describing links between content-addressed data, like IPFS files, Git commits, or Ethereum blocks.
- [The Permissive License Stack](https://protocol.ai/blog/announcing-the-permissive-license-stack) is a licensing strategy for software development that embraces open-source values.

### 相关项目

libp2p 最初是 [IPFS](https://ipfs.io) 项目的一部分，现在仍然是 IPFS 的重要组成部分。因此，libp2p 可以与 IPFS “家族”中其他项目提供的抽象和工具很好地组合在一起。 检查其各个站点以获取特定信息和参考：

-[IPFS](https://libp2p.io) 是星际文件系统，它使用 libp2p 作为其网络层。
-[Multiformats](https://multiformats.io) 是多种*自描述*数据格式。
-[IPLD](https://ipld.io) 是一组工具，用于描述内容寻址数据之间的链接，例如 IPFS 文件，Git 提交或以太坊区块。
-[The Permissive License Stack](https://protocol.ai/blog/announcing-the-permissive-license-stack) 是具有开源价值的软件开发许可策略。
