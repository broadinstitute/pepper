## What's Pepper?

Pepper is an open-source platform for building high quality, scalable, cross-platform, and secure direct-to-participant studies for human subjects research.  Pepper is the software foundation of a growing number of patient-partnered research studies operating at the Broad Institute and beyond.

We encourage you to use our deployed instance of pepper to host your studies, but if you would like to spin up your own instance of Pepper, you are welcome to do so.  We feel that in the interests of democratizing access to patient partnered research, sharing our code is the right thing to do, even though we do not currently offer support for standing up your own instance.

We are also happy to look at pull requests, although our ability to do so is limited at this time.  Please adhere to our [code of conduct](https://github.com/broadinstitute/pepper/blob/master/code_of_conduct.md) at all times.

Pepper is a team effort, and we are grateful to the many wonderful people who have contributed to it over the years, in particular:

* Mikhail Aleksandrov
* Cameron Ardell
* Esme Baker
* Charlotte Dye
* Edgar Galstyan
* Erin Gwozdz
* Diane Kaplan
* Nadya Lopez Zalda
* Jen Lapan
* Simone Maiwald
* Richard Nordin
* Marco Ocana
* Sergei Retsia
* Sampath Settipalli
* Pavel Sidorenko
* Blake Skinner
* Pegah Taheri
* Yufeng Wang
* Kiara Westbrooks
* Andrew Zimmer


## Components

We believe in loose coupling and the ability to innovate, so rather than bundling everything together, we have backend APIs and SDKs.  Hopefully you find the SDKs helpful, but if they are too constraining, you can always drop back to the APIs directly.

### [Study Server](https://github.com/broadinstitute/ddp-study-server)
The study server is where participant-reported information is stored and managed using our APIs.  The study server also manages participant-facing workflows and reminders.

### [Study Manager](https://github.com/broadinstitute/ddp-study-manager)
Study staff interact with the study manager to review the status of participants and keep track of logistics such as form completion, medical records and kit logistics, abstraction, and review participant-reported data.

### SDKs: [Angular](https://github.com/broadinstitute/ddp-angular), [iOS](https://github.com/broadinstitute/pepper-ios-sdk), and [Android](https://github.com/broadinstitute/ddp-android-sdk)
Pepper's SDKs provide more fluent ways to interact with the backend, and provide glue between backend APIs and Angular web apps, native iOS, and native Android.

## Architecture

We rely on docker and are in the process of moving towards google app engine to simplify deployment, compliance, and reduce operational costs.   The Study Manager and Study Server communicate with one another directly, as well as through Elastic.  Participant-facing applications primarily interact with the study server, while study staff primarily interact with the study manager.  The backend of Pepper is written in Java and uses relational storage for well-structured data such as patient-reported information and abstracted medical records.  Bucket-based storage is used for pretty much everything else.

## Building

Our bandwidth to assist with building the entire platform outside of its current home is extremely limited.  Each repository should have sufficient build instructions for local builds.  However, there are a number of dependencies that we know are challenging to stand up outside of the datadonationplatform.org due to logistical constraints.  Our primary deployment at pepper.datadonationplatform.org is where we focus our efforts, so the investment we have made in making the platform easy to build and deploy _outside_ of its current home is minimal.  In general, we would prefer to see code contributions and use of the multitenant instance as it is routinely monitored both for uptime as well as security, and using a shared instance will be less expensive to operate than deploying your own.  That said, PRs that streamline builds and deploys are very welcome!

#### Vault

We use [vault](https://www.vaultproject.io) to store build secrets.  Our build scripts hardcode vault paths, and tools expect that whoever runs the scripts has sufficient access to vault.  Take a look at `*.conf.ctmpl` files to get a sense of what these values are.  We do not provide rendered example configuration files.

#### Auth0

[Auth0](https://auth0.com) is the backbone for identity management.  In order to deploy a running backend instance, you will need at least one auth0 tenant.  Auth0 has some terrific free options.

#### Sendgrid (Twilio)

Emails from Pepper are sent via [Sendgrid](https://sendgrid.com).  Sendgrid has great free options.

#### EasyPost

We use [EasyPost](https://www.easypost.com) as a shipping aggregator for studies that ship sample collection kits to participants.  You can setup a test account with EasyPost.


