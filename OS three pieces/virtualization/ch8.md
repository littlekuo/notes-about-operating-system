

# 调度：多级反馈对列

多级反馈队列(Multi-level Feedback Queue, MLFQ)。

## MLFQ：基本原则
MLFQ中有许多独立的队列，每个队列有不同的优先级。任何时候，一个工作只能处于一个队列中。MLFQ总是优先执行较高优先级的工作。

规则：
- 如果A的优先级 > B的优先级，运行A
- 如果A的优先级 = B的优先级，轮转A和B
- 工作刚进入系统时，放在最高优先级
- 一旦工作用完了其在某一层中的时间配额，就降低其优先级
- 经过一段时间S，将系统中的所有工作加入到最高优先级队列(避免饥饿)


