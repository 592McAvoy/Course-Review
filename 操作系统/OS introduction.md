# OS Introduction

### 1. Why OS is important?

Operating system is a maturing field→Hard to get people to switch operating systems

Many things are OS issues：

- High-performance
- Resource consumption
- Battery life, radio spectrum
- Security needs a solid foundation
- New “smart” devices need new OS

### 2. 8 important problems

- Scale Up 
  - 纵向扩展，更快运行更多software
  - 实现多核更高性能（受lock、共享数据、共享硬件限制）
  - 对user-app提供更好抽象；消除不可扩展同步；最小化共享资源；
- Scale Out
  - 横向扩展，分布式系统
  - 困难：系统设计；一致性；容错；不同部署场景；安全性；实现；
- Security & Privacy
- Energy Efficiency
- Mobility 
  - 移动端OS：高能源利用率；有限资源；安全问题（更多data存在OS）
- Write Correct (Parallel) Code
- Non-Volatile Storage
- Virtualization
  - 资源复用；容错；轻便；易于管理