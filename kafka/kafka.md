## Apache Kafka

&nbsp;

### Event-Driven Architecture

Architecture that based on Event, where there are program to manage the events and services that consume the events/

&nbsp;

### Event-Driven Architecture

1. Apache Kafka is used to manage and process events.
2. Producer listens to apps and then write to kafka cluster.
3. Events are immutable

- Kafka cluster => Made of brokers
- Brokers => Individual server, with own disks/local storage

3. Consumer reads from kafka cluster.
4. This diagram may lead to a similar ESB (Enterprise Service Bus) diagram.

&nbsp;

### Topics

1. Topic is a related "messages"/events (stream of related events).
2. Partition is a part of distributed Topics. (essentially LOGS).
3. Kafka then allocate partition to a different brokers.
4. Partition is then broken down to segments.
5. So essentially individual files on brokers is a segment.
6. Key - Value pair => Kafka data model

&nbsp;

### Brokers

1. Manage partitions
2. Broker does replicate for reliability.
3. They does it in Leader-Follower fashion.

&nbsp;

### Producers

1. Default partitioning strategy by producers => hash (key) % num_partition
2. Partitioning strategy used for load balancing

### Consumers

1. Reads data
2. There are offsets, so Topics customer offsets is on kafka cluster to help consumer remember

- Data being kept by default in 1 week, and can be changed.
- Segments are the ones being deleted in retention policy.

## Producers Guarantees on brokers

1. None acknowledgements
2. Leader acknowledgements
3. All acknowledgements (from followers too)

## Compacted Topics

- The most recent topic only. So when you change something, it only takes the most recent one
