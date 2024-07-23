---
description: How to use Phalcon in one minute
---

# Quick Start

Using BlockSec Phalcon is straightforward; it only consists of three steps: adding contracts, monitors, and actions. After that, everything is settled, and you have a 7x24 security bot to help you secure your protocol and assets. This document will show you how to use Phalcon quickly.&#x20;

## Basic Concepts

The user must add Contracts to Phalcon and a **Monitor** or Multiple **Monitors** for each contract. A monitor's triggering conditions are based on BlockSec's _security engine results_ and the u_ser-configured monitoring rules_.&#x20;

For each transaction inside the mempool that will interact with the Contract and the transactions confirmed on the blockchain that have interacted with the Contract, Phalcon will check the _triggering condition_s for Monitors. When the triggering condition is satisfied, a notification will be sent to user-configured **Notification Channels**, and (or) user-defined automatic **Actions** will be fired. The automatic **Action** can be used to _pause the contract, make the contract circle-break, withdraw funds, and others._ &#x20;

## Add Contract





