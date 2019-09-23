## Project name and description

Akkeris is a "self-service" developer experience for deploying and 
managing applications in the cloud. It's a combination of six distinct
and independent (but interoperational) projects:

* Build Shuttle - A project that builds images automatically from commits within Github and streams its logs to an S3 or Kafka system.
* Log Shuttle - A system that streams kubernetes pod logs (for one or more deployments) from fluentd, build logs from build shuttle, system events (e.g., crashes) and OSB logs to an endpoint (syslog, https, tls+syslog) that can be added and removed dynamically via an API.
* OSB Brokers - Open service brokers for AWS and GCloud Postgres, MySQL, MongoDB, Redis and Memcached instances.
* Business Management - Handles compliance (adding and removing secrets stored in third-party vault systems to deployments, protection against deletion of production resources; not authentication, identity or authorization), status checks, audits, and invoices (attribution and cost reports/analysis).
* Application Lifecycle Management - Pipelining (pushing a QA image to one or more downstream production deployments), invoking tests (TaaS or testing as a service), webhooks, environment variable changes, app creation/deletion, resource provisioning, preview applications (e.g., apps created based on pull requests to a source repo), and canary apps.

In addition, a CLI and UI are provided to interafce with all of the above (however a direct declarative or imperative API is optionally available).

The project was initially created in August of 2016 and has grown from in use at O.C. Tanner (the main contributor) to being used in production by other companies.

## Alignment with CNCF charter mission

The mission of akkeris aligns closely with that of the CNCF. Akkeris has aimed to be
observable, vendor neutral, transparent (no hidden interfaces, and upfront on our roadmap) 
and enabling. 

One aspect that may deviate from CNCF's charter mission is the adherence to 12-factor 
philosophy of app development that Akkeris mandates. [Best Practices and Guildlines for Akkeris](https://docs.akkeris.io/best-practices-and-guidelines.html#introduction).

## Comparison with Similar Projects

* Cloud Foundary offers similar functionality, but its Business Management layer is less robust (attribution and invoicing in addition to compliance does not appear to be available) and does not appear to be aligned with the CNCF (from a technical standpoint it supports far less existing CNCF components).
* Heroku (while not open source, but a SaaS platform) offers similar service but is not open source, nor does it have the same compliance, and sites and route configuration capability, in addition an obvious vendor lock-in.
* Flux does seem to potentially compete as it performs various CI/CD tasks that overlap with some aspects of the Build Shuttle. However the two could easily co-exist.

## Sponsor from TOC

NONE, however, we're hoping to find a mentor in CNCF to help guide the project to grow into something larger that can fit within the CNCF eco-system.

## Preferred maturity level

Sandbox

## License

[Apache 2.0 license](https://github.com/akkeris/contrller-api/blob/master/LICENSE).

## Source control

https://github.com/akkeris (all projects are licensed under the Apache 2)

## External Dependencies

### Linked dependencies:

* Golang
* Node.js
* UI (NPM)
```
    "@auth0/s3": "^1.0.0",
    "@material-ui/core": "^4.1.1",
    "@material-ui/docs": "4.0.0-beta.0",
    "@material-ui/icons": "^4.2.0",
    "ansi-to-react": "^4.0.4",
    "autosuggest-highlight": "^3.1.1",
    "axios": "0.18.0",
    "babel-polyfill": "6.26.0",
    "body-parser": "1.18.3",
    "connect-redis": "3.4.0",
    "crypto-js": "3.1.9-1",
    "deepmerge": "^3.2.0",
    "express": "4.16.4",
    "express-http-proxy": "1.5.0",
    "express-session": "1.15.6",
    "history": "^4.7.2",
    "jsonminify": "0.4.1",
    "parse-github-url": "^1.0.2",
    "prop-types": "15.6.2",
    "react": "^16.8.6",
    "react-autosuggest": "^9.4.2",
    "react-dom": "^16.6.3",
    "react-event-listener": "^0.6.4",
    "react-lazylog": "^3.1.4",
    "react-loadable": "5.5.0",
    "react-router-dom": "^4.3.1",
    "react-select": "^2.3.0",
    "recharts": "1.3.6",
    "recompose": "^0.30.0",
    "request": "2.88.0",
    "testcafe": "1.2.0",
    "testcafe-browser-provider-selenium": "^0.4.0",
    "testcafe-react-selectors": "0.0.8-alpha3",
    "transfer-webpack-plugin": "0.1.4",
    "webpack": "^4.25.1",
    "webpack-cli": "^3.1.2",
    "webpack-dev-middleware": "3.4.0",
    "webpack-hot-middleware": "2.24.3"
```
* CLI (NPM)
```
    "chart": "github:jstrace/chart",
    "cli-table": "^0.3.1",
    "cliui": "^3.2.0",
    "colors": "^1.3.3",
    "crypto-js": "^3.1.9-1",
    "fuzzy": "^0.1.3",
    "inquirer": "^6.2.2",
    "inquirer-autocomplete-prompt": "^1.0.1",
    "netrc": "^0.1.4",
```
* Apps Watcher (NPM)
```
    "@kubernetes/client-node": "^0.10.2",
    "byline": "^5.0.0",
    "node-vault": "^0.8.0",
    "request": "^2.83.0"
```
* Controller (NPM)
```
    "elasticsearch": "^15.1.1",
    "pg": "^7.5.0",
    "uuid": "^2.0.2"
```

* Build Shuttle (NPM)
```
    "@kubernetes/client-node": "^0.10.2",
    "aws-sdk": "^2.422.0",
    "body-parser": "^1.18.3",
    "chai": "^4.2.0",
    "debug": "^4.1.1",
    "dockerode": "^2.5.8",
    "express": "^4.16.4",
    "kafka-node": "^4.0.2",
    "ngrok": "^3.2.5",
    "request": "^2.88.0",
    "request-promise-native": "^1.0.7",
    "uuid": "^3.1.0"
```

* OSB Database Broker (Golang)
```
	cloud.google.com/go v0.32.0
	github.com/aws/aws-sdk-go v1.15.69
	github.com/beorn7/perks v0.0.0-20180321164747-3a771d992973
	github.com/ghodss/yaml v1.0.0
	github.com/go-sql-driver/mysql v1.4.1
	github.com/gogo/protobuf v1.1.1
	github.com/golang/glog v0.0.0-20160126235308-23def4e6c14b
	github.com/golang/protobuf v1.2.0
	github.com/google/btree v1.0.0
	github.com/google/gofuzz v0.0.0-20170612174753-24818f796faf
	github.com/googleapis/gnostic v0.2.0
	github.com/gopherjs/gopherjs v0.0.0-20181103185306-d547d1d9531e
	github.com/gorilla/context v1.1.1
	github.com/gorilla/mux v1.6.2
	github.com/gregjones/httpcache v0.0.0-20180305231024-9cad4c3443a7
	github.com/imdario/mergo v0.3.6
	github.com/jmespath/go-jmespath v0.0.0-20160202185014-0b12d6b521d8
	github.com/json-iterator/go v1.1.5
	github.com/jtolds/gls v4.20.0+incompatible
	github.com/kubernetes/client-go v6.0.0+incompatible
	github.com/lib/pq v1.0.0
	github.com/matttproud/golang_protobuf_extensions v1.0.1
	github.com/modern-go/concurrent v0.0.0-20180306012644-bacd9c7ef1dd
	github.com/modern-go/reflect2 v0.0.0-20180701023420-4b7aa43c6742
	github.com/petar/GoLLRB v0.0.0-20130427215148-53be0d36a84c
	github.com/peterbourgon/diskv v2.0.1+incompatible
	github.com/pmorie/go-open-service-broker-client v0.0.0-20180928143052-79b374a2302f
	github.com/pmorie/osb-broker-lib v0.0.0-20180423193413-f4ca270ef323
	github.com/prometheus/client_golang v0.8.0
	github.com/prometheus/client_model v0.0.0-20180712105110-5c3871d89910
	github.com/prometheus/common v0.0.0-20181020173914-7e9e6cabbd39
	github.com/prometheus/procfs v0.0.0-20181005140218-185b4288413d
	github.com/shawn-hurley/osb-broker-k8s-lib v0.0.0-20180430125558-bed19ac36ffe
	github.com/smartystreets/assertions v0.0.0-20180301161246-7678a5452ebe
	github.com/smartystreets/goconvey v0.0.0-20170602164621-9e8dc3f972df
	github.com/spf13/pflag v1.0.3
	github.com/stackimpact/stackimpact-go v2.3.10+incompatible
	golang.org/x/crypto v0.0.0-20181106171534-e4dc69e5b2fd
	golang.org/x/net v0.0.0-20181106065722-10aee1819953
	golang.org/x/oauth2 v0.0.0-20181106182150-f42d05182288
	golang.org/x/sys v0.0.0-20181106135930-3a76605856fd
	golang.org/x/text v0.3.0
	golang.org/x/time v0.0.0-20180412165947-fbb02b2291d2
	google.golang.org/api v0.0.0-20181102150758-04bb50b6b83d
	google.golang.org/appengine v1.3.0
	gopkg.in/inf.v0 v0.9.1
	gopkg.in/yaml.v2 v2.2.1
	k8s.io/api v0.0.0-20181102122915-de5c567eef5c
	k8s.io/apimachinery v0.0.0-20181101131016-0aa9751e8aaf
	k8s.io/client-go v9.0.0+incompatible
```

* Cache OSB Broker (Golang)
```
	github.com/aws/aws-sdk-go v1.19.32
	github.com/docker/spdystream v0.0.0-20160310174837-449fdfce4d96 // indirect
	github.com/elazarl/goproxy v0.0.0-20170405201442-c4fc26588b6e // indirect
	github.com/evanphx/json-patch v0.0.0-20190203023257-5858425f7550 // indirect
	github.com/ghodss/yaml v1.0.0 // indirect
	github.com/gogo/protobuf v0.0.0-20171007142547-342cbe0a0415 // indirect
	github.com/golang/glog v0.0.0-20160126235308-23def4e6c14b
	github.com/golang/groupcache v0.0.0-20160516000752-02826c3e7903 // indirect
	github.com/google/btree v1.0.0 // indirect
	github.com/google/go-cmp v0.3.0 // indirect
	github.com/google/gofuzz v0.0.0-20170612174753-24818f796faf // indirect
	github.com/google/uuid v1.0.0 // indirect
	github.com/googleapis/gnostic v0.2.0 // indirect
	github.com/gorilla/mux v1.7.1
	github.com/gregjones/httpcache v0.0.0-20190212212710-3befbb6ad0cc // indirect
	github.com/hashicorp/golang-lru v0.5.0 // indirect
	github.com/howeyc/gopass v0.0.0-20170109162249-bf9dde6d0d2c // indirect
	github.com/imdario/mergo v0.3.7 // indirect
	github.com/json-iterator/go v0.0.0-20180701071628-ab8a2e0c74be // indirect
	github.com/juju/ratelimit v1.0.1 // indirect
	github.com/kubernetes/client-go v6.0.0+incompatible // indirect
	github.com/lib/pq v1.1.1
	github.com/modern-go/concurrent v0.0.0-20180306012644-bacd9c7ef1dd // indirect
	github.com/modern-go/reflect2 v1.0.1 // indirect
	github.com/mxk/go-flowrate v0.0.0-20140419014527-cca7078d478f // indirect
	github.com/onsi/gomega v0.0.0-20190113212917-5533ce8a0da3 // indirect
	github.com/peterbourgon/diskv v2.0.1+incompatible // indirect
	github.com/pmorie/go-open-service-broker-client v0.0.0-20180928143052-79b374a2302f
	github.com/pmorie/osb-broker-lib v0.0.0-20180423193413-f4ca270ef323
	github.com/prometheus/client_golang v0.9.2
	github.com/shawn-hurley/osb-broker-k8s-lib v0.0.0-20180430125558-bed19ac36ffe
	github.com/spf13/pflag v1.0.3 // indirect
	github.com/stackimpact/stackimpact-go v2.3.10+incompatible
	golang.org/x/crypto v0.0.0-20190513172903-22d7a77e9e5f // indirect
	golang.org/x/oauth2 v0.0.0-20190402181905-9f3314589c9a // indirect
	golang.org/x/text v0.3.2 // indirect
	golang.org/x/time v0.0.0-20190308202827-9d24e82272b4 // indirect
	gopkg.in/inf.v0 v0.9.0 // indirect
	k8s.io/api v0.0.0-20190503184017-f1b257a4ce96 // indirect
	k8s.io/apimachinery v0.0.0-20180621070125-103fd098999d // indirect
	k8s.io/client-go v0.0.0-20190503184104-3ec0d5188431
	k8s.io/kube-openapi v0.0.0-20190228160746-b3a7cee44a30 // indirect
	k8s.io/utils v0.0.0-20190506122338-8fab8cb257d5 // indirect
	sigs.k8s.io/yaml v1.1.0 // indirect
```

* ElastiSearch OSB Broker (Golang)
```
	github.com/aws/aws-sdk-go v1.19.32
	github.com/docker/spdystream v0.0.0-20160310174837-449fdfce4d96 // indirect
	github.com/elazarl/goproxy v0.0.0-20170405201442-c4fc26588b6e // indirect
	github.com/evanphx/json-patch v0.0.0-20190203023257-5858425f7550 // indirect
	github.com/ghodss/yaml v1.0.0 // indirect
	github.com/gogo/protobuf v0.0.0-20171007142547-342cbe0a0415 // indirect
	github.com/golang/glog v0.0.0-20160126235308-23def4e6c14b
	github.com/golang/groupcache v0.0.0-20160516000752-02826c3e7903 // indirect
	github.com/google/btree v1.0.0 // indirect
	github.com/google/go-cmp v0.3.0 // indirect
	github.com/google/gofuzz v0.0.0-20170612174753-24818f796faf // indirect
	github.com/google/uuid v1.0.0 // indirect
	github.com/googleapis/gnostic v0.2.0 // indirect
	github.com/gorilla/mux v1.7.1
	github.com/gregjones/httpcache v0.0.0-20190212212710-3befbb6ad0cc // indirect
	github.com/hashicorp/golang-lru v0.5.0 // indirect
	github.com/howeyc/gopass v0.0.0-20170109162249-bf9dde6d0d2c // indirect
	github.com/imdario/mergo v0.3.7 // indirect
	github.com/json-iterator/go v0.0.0-20180701071628-ab8a2e0c74be // indirect
	github.com/juju/ratelimit v1.0.1 // indirect
	github.com/kubernetes/client-go v6.0.0+incompatible // indirect
	github.com/lib/pq v1.1.1
	github.com/modern-go/concurrent v0.0.0-20180306012644-bacd9c7ef1dd // indirect
	github.com/modern-go/reflect2 v1.0.1 // indirect
	github.com/mxk/go-flowrate v0.0.0-20140419014527-cca7078d478f // indirect
	github.com/nu7hatch/gouuid v0.0.0-20131221200532-179d4d0c4d8d
	github.com/onsi/gomega v0.0.0-20190113212917-5533ce8a0da3 // indirect
	github.com/peterbourgon/diskv v2.0.1+incompatible // indirect
	github.com/pmorie/go-open-service-broker-client v0.0.0-20180928143052-79b374a2302f
	github.com/pmorie/osb-broker-lib v0.0.0-20180423193413-f4ca270ef323
	github.com/prometheus/client_golang v0.9.2
	github.com/shawn-hurley/osb-broker-k8s-lib v0.0.0-20180430125558-bed19ac36ffe
	github.com/spf13/pflag v1.0.3 // indirect
	github.com/stackimpact/stackimpact-go v2.3.10+incompatible
	golang.org/x/crypto v0.0.0-20190513172903-22d7a77e9e5f // indirect
	golang.org/x/oauth2 v0.0.0-20190402181905-9f3314589c9a // indirect
	golang.org/x/text v0.3.2 // indirect
	golang.org/x/time v0.0.0-20190308202827-9d24e82272b4 // indirect
	gopkg.in/inf.v0 v0.9.0 // indirect
	k8s.io/api v0.0.0-20190503184017-f1b257a4ce96 // indirect
	k8s.io/apimachinery v0.0.0-20180621070125-103fd098999d // indirect
	k8s.io/client-go v0.0.0-20190503184104-3ec0d5188431
	k8s.io/kube-openapi v0.0.0-20190228160746-b3a7cee44a30 // indirect
	k8s.io/utils v0.0.0-20190506122338-8fab8cb257d5 // indirect
	sigs.k8s.io/yaml v1.1.0 // indirect
```

* Logshuttle/Logsession (Golang)
```
	github.com/codegangsta/inject v0.0.0-20150114235600-33e0aa1cb7c0 // indirect
	github.com/confluentinc/confluent-kafka-go v1.1.0
	github.com/go-martini/martini v0.0.0-20170121215854-22fa46961aab
	github.com/gopherjs/gopherjs v0.0.0-20190309154008-847fc94819f9
	github.com/jtolds/gls v4.20.0+incompatible
	github.com/lib/pq v1.0.0
	github.com/martini-contrib/binding v0.0.0-20160701174519-05d3e151b6cf
	github.com/martini-contrib/render v0.0.0-20150707142108-ec18f8345a11
	github.com/nu7hatch/gouuid v0.0.0-20131221200532-179d4d0c4d8d
	github.com/oxtoacart/bpool v0.0.0-20190530202638-03653db5a59c // indirect
	github.com/smartystreets/assertions v0.0.0-20180301161246-7678a5452ebe
	github.com/smartystreets/goconvey v0.0.0-20170602164621-9e8dc3f972df
	github.com/stackimpact/stackimpact-go v2.3.10+incompatible
	gopkg.in/bsm/ratelimit.v1 v1.0.0-20160220154919-db14e161995a
	gopkg.in/redis.v4 v4.2.4
```

* Region API (Golang)
```
	github.com/akkeris/vault-client v0.0.0-20180727165111-6788ec8d1925
	github.com/aws/aws-sdk-go v1.15.52
	github.com/bitly/go-simplejson v0.5.0
	github.com/codegangsta/inject v0.0.0-20140425184007-37d7f8432a3e
	github.com/fatih/structs v1.1.0
	github.com/go-ini/ini v1.38.3
	github.com/go-martini/martini v0.0.0-20140519164645-49411a5b6468
	github.com/gocql/gocql v0.0.0-20181011060509-26b68fd73104
	github.com/golang/glog v0.0.0-20160126235308-23def4e6c14b
	github.com/golang/snappy v0.0.0-20180518054509-2e65f85255db
	github.com/gopherjs/gopherjs v0.0.0-20181004151105-1babbf986f6f
	github.com/hailocab/go-hostpool v0.0.0-20160125115350-e80d13ce29ed
	github.com/jmcvetta/napping v3.2.0+incompatible
	github.com/jmespath/go-jmespath v0.0.0-20160202185014-0b12d6b521d8
	github.com/jtolds/gls v4.20.0+incompatible
	github.com/lib/pq v1.0.0
	github.com/martini-contrib/auth v0.0.0-20150219114609-fa62c19b7ae8
	github.com/martini-contrib/binding v0.0.0-20160701174519-05d3e151b6cf
	github.com/martini-contrib/render v0.0.0-20150707142108-ec18f8345a11
	github.com/nu7hatch/gouuid v0.0.0-20131221200532-179d4d0c4d8d
	github.com/octanner/f5er v0.0.0-20190122181703-99e01a9fd236
	github.com/oxtoacart/bpool v0.0.0-20150712133111-4e1c5567d7c2
	github.com/pmorie/go-open-service-broker-client v0.0.0-20180912182616-9cc214e88d00
	github.com/robfig/cron v1.1.0
	github.com/smartystreets/assertions v0.0.0-20180301161246-7678a5452ebe
	github.com/smartystreets/goconvey v0.0.0-20170602164621-9e8dc3f972df
	github.com/stackimpact/stackimpact-go v2.3.10+incompatible
	gopkg.in/guregu/null.v3 v3.4.0
	gopkg.in/inf.v0 v0.9.1
	gopkg.in/mgo.v2 v2.0.0-20190816093944-a6b53ec6cb22
```

* S3/Minio OSB Broker (Golang)
```
	github.com/aws/aws-sdk-go v1.19.32
	github.com/docker/spdystream v0.0.0-20160310174837-449fdfce4d96 // indirect
	github.com/elazarl/goproxy v0.0.0-20170405201442-c4fc26588b6e // indirect
	github.com/evanphx/json-patch v0.0.0-20190203023257-5858425f7550 // indirect
	github.com/ghodss/yaml v1.0.0 // indirect
	github.com/gogo/protobuf v0.0.0-20171007142547-342cbe0a0415 // indirect
	github.com/golang/glog v0.0.0-20160126235308-23def4e6c14b
	github.com/golang/groupcache v0.0.0-20160516000752-02826c3e7903 // indirect
	github.com/google/btree v1.0.0 // indirect
	github.com/google/go-cmp v0.3.0 // indirect
	github.com/google/gofuzz v0.0.0-20170612174753-24818f796faf // indirect
	github.com/google/uuid v1.0.0 // indirect
	github.com/googleapis/gnostic v0.2.0 // indirect
	github.com/gorilla/mux v1.7.1
	github.com/gregjones/httpcache v0.0.0-20190212212710-3befbb6ad0cc // indirect
	github.com/hashicorp/golang-lru v0.5.0 // indirect
	github.com/howeyc/gopass v0.0.0-20170109162249-bf9dde6d0d2c // indirect
	github.com/imdario/mergo v0.3.7 // indirect
	github.com/json-iterator/go v0.0.0-20180701071628-ab8a2e0c74be // indirect
	github.com/juju/ratelimit v1.0.1 // indirect
	github.com/kubernetes/client-go v6.0.0+incompatible // indirect
	github.com/lib/pq v1.1.1
	github.com/modern-go/concurrent v0.0.0-20180306012644-bacd9c7ef1dd // indirect
	github.com/modern-go/reflect2 v1.0.1 // indirect
	github.com/mxk/go-flowrate v0.0.0-20140419014527-cca7078d478f // indirect
	github.com/nu7hatch/gouuid v0.0.0-20131221200532-179d4d0c4d8d
	github.com/onsi/gomega v0.0.0-20190113212917-5533ce8a0da3 // indirect
	github.com/peterbourgon/diskv v2.0.1+incompatible // indirect
	github.com/pmorie/go-open-service-broker-client v0.0.0-20180928143052-79b374a2302f
	github.com/pmorie/osb-broker-lib v0.0.0-20180423193413-f4ca270ef323
	github.com/prometheus/client_golang v0.9.2
	github.com/shawn-hurley/osb-broker-k8s-lib v0.0.0-20180430125558-bed19ac36ffe
	github.com/spf13/pflag v1.0.3 // indirect
	github.com/stackimpact/stackimpact-go v2.3.10+incompatible
	golang.org/x/crypto v0.0.0-20190513172903-22d7a77e9e5f // indirect
	golang.org/x/oauth2 v0.0.0-20190402181905-9f3314589c9a // indirect
	golang.org/x/text v0.3.2 // indirect
	golang.org/x/time v0.0.0-20190308202827-9d24e82272b4 // indirect
	gopkg.in/inf.v0 v0.9.0 // indirect
	k8s.io/api v0.0.0-20190503184017-f1b257a4ce96 // indirect
	k8s.io/apimachinery v0.0.0-20180621070125-103fd098999d // indirect
	k8s.io/client-go v0.0.0-20190503184104-3ec0d5188431
	k8s.io/kube-openapi v0.0.0-20190228160746-b3a7cee44a30 // indirect
	k8s.io/utils v0.0.0-20190506122338-8fab8cb257d5 // indirect
	sigs.k8s.io/yaml v1.1.0 // indirect
```

* Service Watchers
```
	github.com/akkeris/vault-client v0.0.0-20180727165111-6788ec8d1925
	github.com/bitly/go-simplejson v0.5.0
	github.com/stackimpact/stackimpact-go v2.3.10+incompatible
	k8s.io/api v0.0.0-20190620084959-7cf5895f2711
	k8s.io/apimachinery v0.0.0-20190612205821-1799e75a0719
	k8s.io/client-go v0.0.0-20190620085101-78d2af792bab
```


### Non-linked dependencies:

* (required) Istio/Envoy and/or BigIP F5 for Gateway Management
* (required) Kubernetes for Runtime
* (required) Cert Manager
* (required) Harbor, Quay or Docker Registry for storing runtime images
* (optional) Vault (for secret management)
* (optional) Github/Git for SCM

## Initial committers

Trevor Linton (OC Tanner), Murray Resinski (OC Tanner)

## Infrastructure requests

There are no infrastructure requests; Akkeris uses circleci for
tests and releases.

## Communication channels

Development discussion is done via Slack channel available to the
public, in addition opening issues on Github: https://github.com/akkeris/akkeris/issues

## Issue tracker

In the [GitHub project](https://github.com/akkeris/akkeris/issues).

## Website

None at present; documentation is at [GitHub
repo](https://docs.akkeris.io).

## Release methodology and mechanics

Container images are built via CircleCI and installation and upgrades are done via four helm charts.

## Social media accounts

None.

## Community size and existing sponsorship

Two existing medium to small corporate users, one corporate sponsor and a couple dozen fly-by contributors.

## Who is currently known to be using this?

O.C. Tanner (who is currently funding maintenance on it), uses it in production for 1,000 microservices deployed in the separate countries. In additional Big Squid a analytics start up. Collectively the user base is over 300 engineers.

## Project logo

A WIP logo: https://avatars3.githubusercontent.com/u/33560024?s=200&v=4
