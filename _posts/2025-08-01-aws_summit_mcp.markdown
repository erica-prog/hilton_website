---
layout: post
title: From Cloud Infrastructure to Autonomous Agents - AWS Summit 2025 Experience
description: Exploring the cutting edge of AI automation at AWS Summit Washington D.C. and MCP workshop at a Gen AI DC Meetup. 
date: 2025-02-29 15:01:35 +0300
image: '/post_images/cover_images/aws_summit_cover.png'
tags: [technology, ai, aws, data-science]
---

The landscape of AI and cloud computing is rapidly evolving from simple text generation to autonomous action-taking systems. At the recent AWS Summit in Washington, D.C., alongside a specialized Model Context Protocol (MCP) workshop, I witnessed firsthand how AWS is positioning itself at the forefront of this transformation. This article explores how AWS's latest tools—from Bedrock to the emerging Strands Agents framework—are enabling developers to build truly autonomous AI systems that don't just think, but act.

## Section 1: AWS Summit Overview 

**The AWS Summit Experience**

It was a two-day deep dive into AWS cloud services, featuring hands-on workshops and an opportunity to speak with companies on the Expo floor, like Datadog, Snowflake, Nvidia, Accenture, Booz Allen, and many more, about their products and how they interact with AWS.

<div class="gallery-box">
  <div class="gallery">
    <img src="/post_images/aws_summit/aws_summit_expo.jpg" loading="lazy">
  </div>
  <em>AWS Summit Expo Floor - Networking with industry leaders</em>
</div>

A workshop led by AWS Solution Architects Tushar J. and Sohaib T. on **NET202 (Leveraging Generative AI for AWS Networks)**, this session walked through how to integrate Amazon's Generative AI Stack into network automation workflows. This is not just about individual services; it is an integrated architecture that enables autonomous AI systems.


The key takeaways from the AWS Generative AI Stack Architecture include:

- **Amazon Q Business & Q Developer** serve as the user-facing productivity boosters that demonstrate the practical value of AWS's AI infrastructure. Q Business transforms how organizations access and synthesize information across their entire data ecosystem, while Q Developer goes beyond code completion to understand entire architectures and generate production-ready code optimized for AWS services. These applications showcase AI moving from simple text generation to context-aware business intelligence.

- **Amazon Bedrock** functions as the centralized experimentation studio and model customization platform. Rather than forcing organizations into a single model provider, Bedrock offers access to foundation models from Anthropic and others through a unified API. Moreover, it enables fine-tuning with custom datasets and retrieval-augmented generation (RAG) that connects directly to enterprise data sources.

- The foundation rests on **Amazon SageMaker** for comprehensive ML lifecycle management, **AWS Trainium** for training optimization, and **AWS Inferentia** for high-performance inference. These are purpose-built infrastructure components designed specifically for the computational patterns of modern foundation models. Trainium delivers up to 50% better price-performance for large model training, while Inferentia optimizes for the low-latency, high-throughput requirements of production AI workloads.

What makes this architecture significant is its design intent: enabling autonomous software systems that can reason, plan, and execute actions independently. The workshop demonstrations expressed that AI agents monitor infrastructure, making capacity decisions and executing tasks without human intervention.

The stack's integration with emerging standards like the Model Context Protocol (MCP) positions it to support the next generation of agentic AI workflows—systems that both think and act.

## The Context Challenge

Despite the impressive capabilities demonstrated at AWS Summit, a fundamental limitation became apparent during discussions with data scientists and developers: context window constraints that create a significant gap between AI potential and practical application.

Token limitations remain a critical bottleneck, as GPT-4's 32,000 token limit falls short when dealing with real-world data processing requirements. A typical enterprise CSV file with customer data can easily exceed these limits, forcing data practitioners into manual chunking, preprocessing, and summary workflows that undermine AI's efficiency promise. For example, data scientists exploring large customer datasets find themselves constantly managing what information to include or exclude from their AI analysis. Therefore, this creates the gap between AI capability and practical applications.

This challenge led me to explore a promising solution at the Model Context Protocol (MCP) Server workshop at a Data Science/Gen AI community meetup in DC.

<div class="gallery-box">
  <div class="gallery">
    <img src="/post_images/aws_summit_mcp/mcp_architecture.png" loading="lazy">
  </div>
  <em>MCP Workshop at Data Science/Gen AI Meetup</em>
</div>

The MCP Server workshop in DC introduced a solution that fundamentally changes how AI systems access and process information. Rather than forcing all data through limited context windows, MCP creates a standardized way for AI to access unlimited external resources.

## What is the Model Context Protocol (MCP)?

The Model Context Protocol (MCP) defines an open protocol for normalizing AI-application context exchange, essentially creating a standardized interface that allows any AI system to communicate with any data source or service. Like how USB-C provides a universal connection standard for devices, MCP provides a universal connection standard for AI applications.

The protocol uses a client-server architecture enabling multiple integrations, where AI agents (clients) can connect to multiple MCP servers simultaneously[^1]. Each server can provide access to different resources: databases, APIs, file systems, or web services.

MCP implements this through a JSON-RPC interface for structured AI-world interactions[^2]. Rather than cramming everything into a context window, the AI can make specific, structured requests for information as needed during its reasoning process.

## Technical Architecture

How MCP enables real-world actions beyond text generation represents a fundamental shift in AI system design. Instead of being limited to text responses, MCP-enabled AI can execute database queries and safely call "tools" such as APIs, scripts, or database queries, with the server handling authentication, input validation, and execution. It follows a client-server architecture where a host application can be connected to multiple servers.

The role of pre-built integrations and SDK flexibility makes MCP practical for organizations. Rather than building custom connections for every data source, teams can leverage existing MCP servers for common systems like PostgreSQL, MongoDB, REST APIs, and cloud services. For unique requirements, the SDK flexibility allows rapid development of custom MCP servers.

To facilitate data implementation, the community provides SDKs in multiple languages (e.g., Python, JavaScript) and makes its services open-source. One prominent implementation is **FastMCP**[^3], a Python framework that simplifies the process of building MCP clients and servers. It handles the low-level boilerplate (JSON-RPC handling, concurrency, error handling) so that developers can simply annotate Python functions as tools. FastMCP 2.0 surpasses the base specification, providing features such as server composition, auto-generating tool interfaces from REST APIs, authentication layers, and deployment utilities.

## Building Autonomous Workflows with AWS

A workshop spokesperson demonstrated how AWS Strands Agents and Nova Act, combined with Amazon Bedrock and MCP, can build autonomous agentic workflows on AWS.

**Strands Agents** provide the high-level agent framework with multi-tools, multi-step reasoning, and easy Bedrock integration[^4]. It is an open-source SDK for building AI agents in just a few lines of code. Strands is provider-agnostic and comes with built-in support for many model endpoints. By default, it connects to Amazon Bedrock using Anthropic's Claude 3.7 as the default model. Strands prides itself on being "lightweight yet product-ready." It offers a simple, extensible agent loop and includes full support for observability (tracing, logging) and scalable deployment to AWS Lambda, Fargate, etc.

**Nova Act SDK** provides an interface for AI to perform web browser actions autonomously[^5]. In contrast to general Large Language Models (LLMs) that primarily generate text, Nova Act is trained to understand web pages, their structure (including DOM elements, forms, and buttons), and perform clicks, form entries, and navigation based on natural language instructions. Nova Act's capabilities can be exposed to broader AI systems through MCP. AWS has demonstrated an MCP-compatible server that wraps Nova Act, bridging Nova Act's browser automation with the MCP tool interface. Using this, any AI agent (such as one built with Strands or a chat interface like Claude Desktop) can call Nova Act actions as MCP tools. For example, an agent could issue an MCP request to "search for X on a website and scrape results," which the Nova Act MCP server would execute in a real browser and return the data. 

A practical example of this integration is Accenture's Spotlight platform, which uses Amazon Nova and Bedrock Agents to efficiently personalize content at scale, transforming captured video footage into personalized and marketable content that drives customer engagement.

By combining all these agentic workflows, developers can build powerful autonomous agents on AWS[^6]. The MCP serves as the glue that allows these components to communicate in a standardized and secure way. The outcome is an "agentic" system that can not only think with an LLM but also act on those thoughts, whether by calling APIs, running code, or even driving a web browser to complete tasks. These approaches, demonstrated in AWS workshops and online resources, represent the cutting edge of applied AI in 2025, where agents can deliver end-to-end solutions from cloud data to web automation.

## Implications for Data Science

Many data analysts and researchers face a common challenge when using Large Language Models (LLMs) for data exploration: context length limitations[^7]. While LLMs like GPT-4 (32,000 tokens) and Claude 3.5 (200,000 tokens) have impressive capabilities, they still have fixed context windows that restrict the amount of data they can process simultaneously. This limitation becomes particularly apparent when working with large CSV files.

The convergence of MCP, Strands Agents, and Nova Act represents more than just new AWS services—it signals a fundamental shift toward truly autonomous AI systems. As these technologies mature and integrate further, we're moving from AI that assists to AI that acts independently, transforming how organizations approach everything from data analysis to customer engagement. For data scientists and developers, the question isn't whether to adopt these agentic workflows, but how quickly they can integrate them into their existing infrastructure.


## References

[^1]: Strands Agents Documentation. "Model Context Protocol (MCP) Tools." [https://strandsagents.com/latest/documentation/docs/user-guide/concepts/tools/mcp-tools/](https://strandsagents.com/latest/documentation/docs/user-guide/concepts/tools/mcp-tools/)

[^2]: Model Context Protocol. "Architecture Overview." [https://modelcontextprotocol.io/docs/learn/architecture](https://modelcontextprotocol.io/docs/learn/architecture)

[^3]: Lowin, J. (2024). FastMCP (Version 2.0) [Computer software]. GitHub. [https://github.com/jlowin/fastmcp](https://github.com/jlowin/fastmcp)

[^4]: AWS Open Source Blog. (2025). "Introducing Strands Agents, an Open Source AI Agents SDK." [https://aws.amazon.com/blogs/opensource/introducing-strands-agents-an-open-source-ai-agents-sdk/](https://aws.amazon.com/blogs/opensource/introducing-strands-agents-an-open-source-ai-agents-sdk/)

[^5]: Amazon AGI. (2025). "Introducing Amazon Nova Act" Amazon AGI Labs. [https://labs.amazon.science/blog/nova-act](https://labs.amazon.science/blog/nova-act)

[^6]: AWS Samples. (2025). "Building Agents with Amazon Nova Act and MCP." [https://github.com/aws-samples/sample-agents-with-nova-act-and-mcp](https://github.com/aws-samples/sample-agents-with-nova-act-and-mcp)

[^7]: Avi Chawla. "Found an MCP Server that All Data Analysts Should Know About." LinkedIn. [https://www.linkedin.com/posts/avi-chawla_found-an-mcp-server-that-all-data-analysts-activity-7338876734332669953-YLdl](https://www.linkedin.com/posts/avi-chawla_found-an-mcp-server-that-all-data-analysts-activity-7338876734332669953-YLdl)