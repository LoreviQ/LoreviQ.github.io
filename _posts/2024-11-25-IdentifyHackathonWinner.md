---
layout: post
title: Building IDentify - A Prize Winning Solana Wallet Network Explorer
tags: [python, ai, data analysis, machine learning, nlp]
comments: false
--- 

I recently participated in a [Web3 AI London Hackathon](https://earn.superteam.fun/listings/bounty/web3-ai-summit-code-leverage-ai-to-build-on-solana/), where I built IDentify - a tool that visualizes connections between Solana wallets by analyzing their on-chain interactions. The project won a $500 prize and helped address a crucial challenge in blockchain transparency.

## The Problem

While blockchain transactions are publicly visible, identifying who owns specific wallets remains a significant challenge. This "pseudonymous" nature of crypto can be exploited for scams and illicit activities. We can see everything a wallet has done, but connecting these actions to real-world entities requires complex analysis of transaction patterns and wallet relationships.

## The Solution: IDentify

I built IDentify to help map these relationships. The application:
- Takes any Solana wallet address as input
- Analyzes recent transactions to identify connected wallets
- Creates an interactive visualization of wallet relationships
- Provides detailed transaction statistics and token transfers
- Helps identify patterns and potential connections between wallets

You can try it here: [IDentify Live Demo](https://identify-solana.streamlit.app/)  
Source code: [GitHub Repository](https://github.com/LoreviQ/IDentify)

## Technical Implementation

I built the entire application in just a few hours using:
- Python and Streamlit for the web interface
- Solana RPC API for blockchain data
- NetworkX & Streamlit-AGraph for network visualization
- Pandas for data processing

The application visualizes wallet connections as an interactive graph, with node sizes and edge weights representing the strength of relationships between wallets.

## Hackathon Experience

The Web3 AI London Hackathon provided an excellent opportunity to dive deep into blockchain development while exploring the intersection of crypto, AI, and Web3. While some panels were more engaging than others, the event offered valuable insights into current trends and challenges in the space.

The hackathon's diverse focus on crypto/AI/Web3 topics created an environment where participants could explore innovative solutions. Winning the $500 prize validated the importance of addressing blockchain transparency challenges and demonstrated my ability to quickly deliver practical solutions to real-world problems.

## Looking Forward

IDentify was built as a proof of concept, but there's significant potential for expansion. Future improvements could include machine learning for behavior pattern detection, multi-hop wallet exploration, and integration with known wallet labels.

This project showcases my ability to:
- Rapidly prototype and deliver functional solutions
- Work with blockchain technologies and complex data visualization
- Identify and address real-world challenges in the crypto space
- Successfully compete in hackathon environments

The experience reinforced my passion for building tools that make blockchain technology more accessible and transparent while highlighting the importance of responsible innovation in the Web3 space.

---

The code is open source under the MIT license, and I welcome contributions from the community to help expand its capabilities.