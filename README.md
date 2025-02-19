[![GitHub release](https://img.shields.io/github/release/database-mesh/pisanix.svg)](https://github.com/database-mesh/pisanix/releases)
[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
[![Slack](https://img.shields.io/badge/%20Slack-DatabaseMesh%20Channel-blueviolet)](https://join.slack.com/t/databasemesh/shared_invite/zt-19rhvnxkz-USjZ~am~ghd_Q0q~8bAJXA)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fdatabase-mesh%2Fpisanix.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fdatabase-mesh%2Fpisanix?ref=badge_shield)

> Briefly, if applications want a MySQL, just access `localhost:3306`.

# Introduction

`Pisanix` [Pi-sanics] is a modern database governance framework for Kubernetes. Pisanix adds SQL-aware traffic control, audit, security and extension abilities to help manage various databases in the [Database Mesh](https://www.database-mesh.io) way.

`Pisanix` has *4* major features:

1. *Local Service as Database*: Pisanix provides a local database service, that is one applications could access a MySQL at localhost:3306 without any knowledge of the real data source. 
2. *Unified Config Management*: Pisanix provides a centralized management of Database Mesh configurations, including traffic strategies like read-write splitting, sharding, encryption and concurrency control.
3. *Multi Protocol Support*: Pisanix has a bunch of different plugins to help build a **Glue Layer** for any database protocols. 
4. *Cloud Native Architecture*: Pisanix takes advantage of the classic control plane and data plane pattern, using Infrastructure as Code to make it a versioned database access behavior.

 <img src="static/dbmesh-layer.jpg" width="600" length="600"/>

# Current Status 

Pisanix now supports `TrafficStrategy` of [Database Mesh Specificiation](https://github.com/database-mesh/database-mesh), besides `VirtualDatabase`, `DatabaseEndpoint`, and other features like `AuditRequest` and `AccessControl` are also on the way:

- TrafficStrategy
  - Load Balance  
    - [x] Simple LoadBalance 
    - [x] Read Write Splitting
      - [x] Static 
      - [x] Dynamic
        - [x] Master-Slave Replication
        - [x] MHA
  - Plugins
    - [x] Circuit Break
    - [x] Concurrency Control
- DataStrategy
  - Sharding
    - [x] Sharding with keys  
       - [x] Single Database Sharding Tables  
       - [x] Sharding Databases
       - [ ] Sharding Databases with Sharding Tables
- AuditRequest
  - [ ] Audit with AWS    
- AccessControl
  - [ ] Fine-Grained Access Control   
- QoSClaim  
  - [x] TrafficQoS
 

# Getting Started
- [Quick Start](https://www.pisanix.io/docs/quickstart)

# Highlights

Pisanix has 3 components:

* ***Pisa-Controller***: A Golang control plane designed for sidecar injection and configuration transformation
* ***Pisa-Proxy***: A high performance Rust data plane used as SQL traffic proxy, support various of traffic governance capabilities.
* ***Pisa-Daemon(Coming Soon)***: A optional data plane works on every node, provide programmable runtime management such as TrafficQoS.

 <img src="static/pisanix-arch.png" width="600" length="600"/>

# Goals 

`Pisanix` has the following goals:

1. SQL-Aware Traffic Control: supports SQL traffic load balancing, access control, observability.
2. Runtime Resource-oriented Programming: supports extensible resource control abilities.
3. Database Reliability Engineering: make DBA's life easier with Kubernetes

## Database traffic governance

Applications access databases with SQL, so Pisanix will hijack all SQL traffic. This is a great opportunity to do a lot of things around traffic, like loadbalancing and SQL firewall.

## Observability

In the past, metrics could be retrieved from database instances and display in kinds of charts. Now with Pisanix, DBAs could have more chances to achieve better observability.

## Programmable 

For DBAs who could and would like to solve problems with programming. Pisanix supports many kinds of plugin mechanism, like Lua and Wasm. People will have the chance to 'reshape' the expected behavior of databases.

# Documentation

Full documentation will be available on the [Pisanix website](https://www.pisanix.io/).

# Contribution

Please follows [Contributing Guide](./CONTRIBUTING.md)

# Community & Support

| | |
|:-|:-|
| Mailing List| https://groups.google.com/g/database-mesh |
| Dev Meetings (Starting Feb 16th, 2022), Bi-weekly Wednesday 9:00AM PST|https://meet.google.com/yhv-zrby-pyt |
| Dev Meetings APAC Friendly (Starting April 27th, 2022), Bi-weekly APAC Wednesday 9:00PM GMT+8|https://meeting.tencent.com/dm/6UXDMNsHBVQO |
| Wechat Broker|pisanix|
| Slack |https://join.slack.com/t/databasemesh/shared_invite/zt-19rhvnxkz-USjZ~am~ghd_Q0q~8bAJXA  |
| Meetings Notes |https://bit.ly/39Fqt3x |

- Wechat User Group: Broker wechat to add you into the user group.
 <img src="static/wechat-user-group-broker.jpeg" width="200" length="200"/>

# Roadmap

The Pisanix project is still at an early stage. In the next work, it will focus on enhancing the governance capabilities of traffic, such as data sharding, application data access auditing , and runtime resource QoS, etc. And it will continuously improve the performance and provide an ease of use experience, support plugin extensions to fit different business scenarios.


## License

[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fdatabase-mesh%2Fpisanix.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fdatabase-mesh%2Fpisanix?ref=badge_large)
