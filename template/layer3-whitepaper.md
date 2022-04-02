---
# Front matter
lang: en-US # Use language codes like de, de-DE, en, en-UK, en-US, fr, it, ...
title: 'Layer 3 Decentralized Communication Network'
subtitle: 'A Financial Information eXchange system built on blockchain'
author: 'Louis Bellet'
date: 22-02-2022
abstract: 'Each chain is isolated, forcing users to silo their liquidity and limiting options to move liquidity and state between walled ecosystem. This paper present Layer 3, an overlay network using state-channels for Financial Information eXchange.'
keywords: 'Blockchain, State-Channels, Crypto-Currency, Trading, Clearing, Liquidity'
thanks: 'Thanks to Consensys Mesh Team.'

# Bibliography
csl: https://www.zotero.org/styles/chicago-note-bibliography # See https://www.zotero.org/styles for more styles.
bibliography: references.bib # See https://github.com/jgm/pandoc-citeproc/blob/master/man/pandoc-citeproc.1.md for more formats.
suppress-bibliography: false
link-citations: true
color-links: true # See https://ctan.org/pkg/xcolor for colors
linkcolor: black
urlcolor: black
citecolor: black
endnote: false

# Formatting
toc-title: 'Table of contents'
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
mainfont: # See https://tug.org/FontCatalogue/seriffonts.html for fonts
sansfont: # See https://tug.org/FontCatalogue/sansseriffonts.html for fonts
monofont: # See https://tug.org/FontCatalogue/typewriterfonts.html for fonts
mathfont: # See https://tug.org/FontCatalogue/mathfonts.html for fonts
documentclass: report # See https://www.ctan.org/topic/class
classoption: [notitlepage, onecolumn, openany]
geometry: [a4paper, bindingoffset=0mm, inner=30mm, outer=30mm, top=30mm, bottom=30mm] # See https://ctan.org/pkg/geometry for more options

# LaTeX snippets
header-includes:
  - |
    ```{=latex}
    \linepenalty=10 % the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
    \interlinepenalty=0 % value of the penalty (node) added after each line of a paragraph.
    \hyphenpenalty=50 % the penalty for line breaking at an automatically inserted hyphen
    \exhyphenpenalty=50 % the penalty for line breaking at an explicit hyphen
    \binoppenalty=700 % the penalty for breaking a line at a binary operator
    \relpenalty=500 % the penalty for breaking a line at a relation
    \clubpenalty=150 % extra penalty for breaking after first line of a paragraph
    \widowpenalty=150 % extra penalty for breaking before last line of a paragraph
    \displaywidowpenalty=50 % extra penalty for breaking before last line before a display math
    \brokenpenalty=100 % extra penalty for page breaking after a hyphenated line
    \predisplaypenalty=10000 % penalty for breaking before a display
    \postdisplaypenalty=0 % penalty for breaking after a display
    \floatingpenalty = 20000 % penalty for splitting an insertion (can only be split footnote in standard LaTeX)
    ```
  - |
    ```{=latex}
    \raggedbottom % or \flushbottom
    ```
  - |
    ```{=latex}
    % keep figures where there are in the text
    \usepackage{float} 
    \floatplacement{figure}{H}
    ```
  - |
    ```{=latex}
    % add custom hyphentation rules
    \hyphenation
    {%
      Hyphenate-me-like-this
      Dontyoueverhyphenateme
    }%
    ```
---

# Introduction

Since Bitcoin and Binance, many Engineers and traders work together in crypto,
While most trader only use CEX, the trading occurs in isolated silos, each CEX / DEX has their own markets and unlike traditional finance those markets are not global.

Blockchain has brought decentralized computation, but it far from being able scale to what traditional finance is today, due to the consensus algorithm which requires node to agree on the version of the state.

# Background

Crypto-currency trade is real, but there is no ECN and clearing house to help scaling and interconnecting the whole industry

## Related Work

| Spalte 1            | Spalte 2            | Spalte 3            |
| ------------------- | ------------------- | ------------------- |
| Warum mit innerhalb | Warum mit innerhalb | Warum mit innerhalb |
| dem dieser folgte,  | dem dieser folgte,  | dem dieser folgte,  |
| so Information.     | so Information.     | so Information.     |

Table: Example of table information

### Centralized Exchange

### DyDx

### Uniswap

### Lightning Network

### CELR Network

### Qredo

### LayerZero

Slow, amplify queries, this design illustrate well the complexity of synchronization between chains.

# Design

Mesh network

![The cat.](cat.jpg 'Logo Title Text 1')

## Network participants

### Retail Brokers

A small exchange, located on a specific country or region, comply with local regulations
In our network we define brokers as non-custodial business.

### Market makers

### Exchanges

### Custodian

## System Components

### Network Nodes

### Adjudicators

### Custodians

## Protocol

# Finance

## ECN

## Clearing house

## Cross-currency swap

A cross-currency swap's (XCS's) effective description is a derivative contract, agreed between two counterparties
, which specifies the nature of an exchange of payments benchmarked against two interest rate indexes denominated in two different currencies. It also specifies an initial exchange of notional currency in each different currency and the terms of that repayment of notional currency over the life of the swap

# Conclusions

Blah blah [siehe @jones2016, S. 33-35; auch @sahle2015, Kap. 1].

# References

::: {#refs}
:::
