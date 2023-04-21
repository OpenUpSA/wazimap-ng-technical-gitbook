# NGP2 - Presenting Geographical Hierarchies to users

**NG Proposal 2**

**Representing geographical hierarchies to the user.**

**Proposed by: Adi Eyal**

**Date: 2020-09-02**

**Status: Work in progress**\


## **Context**

Read about Geography Hierarchies [here](system-architecture/geography-hierarchies.md).

The non-linear structure of Geography Hierarchies poses a challenge to presenting information on a map. When in the context of a **Municipality**, the user will either want to see **Wards** or **Mainplaces**. These cannot be shown simultaneously as they overlap with each other. A graphical toggle would be required to change between these two levels.&#x20;

Forks can occur at any part of the hierarchy and are dependent on the current geographical hierarchy in use. For the purpose of illustration, here is a more extensive hierarchy:\


![](https://lh4.googleusercontent.com/m\_NsorMiAHrK42gcglOmNpK9HKPZgTX2vnHpTop16SKmAQtt\_gcYdiNDPwFkRVkyIvFxf9b4pKSTPIYRPV16wu5kD5Opb-YLzbJe-qonldvS2Hiikwx8fKDf7qS\_XxeTo\_Owo-cE)

In this document we discuss the most appropriate user interface to navigate this hierarchy. \


At the time of writing, this is how Wazimap depicts the Wards in the Cape Town metro.&#x20;

![](https://lh3.googleusercontent.com/mqNHRdHj-OpJDr6K2Pkntd0koaSiYYkbmMCNKKdZmmZnPL1cmMfGpRTEwiGBVBFS9d7x-OdteJfdVWNUaky40r27ljzyAGO-Y\_MT7q23d89OrESLfDoqNTMgcsPMY3Ql3mvGpV4L)

Cape Town **Metro** with **Wards** displayed

![](https://lh4.googleusercontent.com/CQ5BsGrxpHXLzP6LQ\_EGoQEa-pnr2jdZ6IVXZi5HjVIEzcTvySscl69CVNpcikMcWNGNg0buC5E7UttXl8GFd7pF8wq8FBliBgvGDSQZDM2pBGBQjbF5haA\_ImHq4rJGb9wlyXFZ)

Cape Town **Metro** with M**ainplaces** displayed\


A typical user requirement would be to switch between **Wards** and **Mainplaces**.\


### **Approach 1**

![](https://lh4.googleusercontent.com/nkv0azQulm7VPF2yVSp4hk0Wo-EaU68qaErJIot0pHdNNoJimYFO\_op3s0rncTebnDK9IpO3PPbadqtYge3ZeLGJcMrPgQJUzEQIVMOh34B6WXE1ut-hwjmJMK7wZcTX8OjzYw\_C)

The first approach to address this is to use a contextual toggle. The select box on the right is populated with the child levels available at the current geography. When the current geography changes, the options change with it.\


This approach requires minor UI changes and can be implemented relatively quickly. Users may however may not necessarily understand the geographical hierarchy and contextual changes may be hard to follow. For example, it may not be obvious that **Subplaces** are not available below Wards.\
\


### **Approach 2**
