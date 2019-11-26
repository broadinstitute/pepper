## What's Pepper?

Pepper is an open-source platform for building high quality, scalable, cross-platform, and secure direct-to-participant studies for human subjects research.  Pepper is the software foundation of a growing number of patient-partnered research studies operating at the Broad Institute and beyond.

We encourage you to use our deployed instance of pepper to host your studies, but if you would like to spin up your own instance of Pepper, you are welcome to do so.  We feel that in the interests of democratizing access to patient partnered research, sharing our code is the right thing to do, even though we do not currently offer support for standing up your own instance.

We are also happy to look at pull requests, although our ability to do so is limited at this time.

## Components

The platform itself is divided into a number of repositories.  We rely on docker and are in the process of moving towards google app engine to simplify deployment, compliance, and reduce operational costs.

We believe in loose coupling and the ability to innovate, so rather than bundling everything together, we have backend APIs and SDKs.  Hopefully you find the SDKs helpful, but if they are too constraining, you can always drop back to the APIs directly.

### Study Server
The study server is where participant-reported information is stored and managed using our APIs.  The study server also manages participant-facing worklows and reminders.

### Study Manager
Study staff interact with the study manager to review the status of participants and keep track of logistics such as form completion, medical records and kit logistics, abstraction, and review participant-reported data.

### SDKs: Angular, iOS, and Android
Pepper's SDKs provide more fluent ways to interact with the backend, and provide glue between backend APIs and Angular web apps, native iOS, and native Android.
