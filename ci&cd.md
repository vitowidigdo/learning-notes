# Devops

- A process of continuous deployment and integration of an app of web, without losing or downtime.

## Devops Engineering Pillars

1. Pull request automation => code reviewers notif and if approved got into the main codebase (using git)
2. Deployment automation => roll new feature to a set of users, roll back to prior version (used spinnaker or harness)
3. Application performance management => So that you can monitor or alert if something goes wrong

## Types of test

1. Unit testing => Ensure individual components work on their own (ex. coffee machine tank hold water?)
2. Integration testing => Ensure a few components work together (ex. coffee machine heater work on tank?)
3. System (end to end) testing => Ensure everything works together (ex. coffe maker brew a cup of coffee?)
4. Acceptance testing => After being launched, does the customer satisfied?

## Continuous Integrations

1. So that developers has reviewers who can see changes on pull requests
2. Have test (TDD) so that reviewers can see if something is wrong
3. Example of testing extension on github is layerCI => So that you just need to have test script (ex: cypress)
4. To view what operation does layerCI do, open yellow dot on related pipeline

## Code Coverage

- Quatitatively measured how comprehensive a code is
- If you want to make changes on a critical code, without breaking the codebase
- The unit test and lines of code to see how much code coverage
- It's a common mistake to make too many tests on uncertain features
- Ex. code coverage tools => Codecov, coveralls, code climate (open source)

## Ephemeral Env

- Temporary deploy where your apps self-contain version is host
- So code reviewer didn't have to set up dev env or ask to screen share with dev that propose the change

## Rolling Deployments

- Deploy new version until all instances of old version is gone
- Delete the old version one by one and replace it with the new one

### Cons of Rolling Deployments

1. Speed
2. API Compatibility (New version of front end go to old version of backend that didn't exist)

- The best way to mitigate it is backward compatibility

### Pros of Rolling Deployments

1. Well Supported
2. No Huge Bursts of Resources
3. Easily Reverted

## Blue Green Deployments

1. Start new instance of app and routing the traffic there.
2. But resource allocations will be quite tricky
3. In blue/green deployment, canary deployment is route 5% of users to the new cluster, and check user's feedback

## Autoscaling vs Serverless

1. Autoscaling is within 1 hour chunks of work.
2. Serverless is autoscaling to the limit, within ~milliseconds

## Service Discovery

1. So that services can talk to each other, finding their IP Addresses
2. Ex. using prod_env in API from frontend
3. There would be down time if you manage it manually from DNS Config,

- Solution:
- Using Reverse proxy, so that the proxy can point rolling or blue green deployments by changing config file in the proxy
- Add key value hash table so that reverse proxy can point there and automatically restart the server if there is new instances
-

## Log Aggregation

1. Collecting all logs from different services to a single dashboard
2. Essence of Log Aggregation => efficiently collect logs from everywhere and make easily search in case of a fault.
3. Ex. ELK (ElasticSearch, Logstash, Kibana) => All logs sent to logstash, store to elasticSearch, send result to Kibana
4. Bonus: ELK can be used for extra tests in CI Pipelines
5. Ex. Another product FluentD (Open Source), DataDog, LogDNA, AWS CloudWatch Dogs

## Metrics Aggregation

1. Data points to tell you how healthy a prod is.
2. If Log Aggregation deals with texts, Metrics deals with numbers
3. Ex. Prometheus
