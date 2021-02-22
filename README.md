<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->

# Apache Ozone **build** environment

This repository contains the definition of a helper container for building [Apache Ozone](https://ozone.apache.org)

Container contains all the required dependencies (and some cached artifacts).

Used by some of the [Github Actions](https://github.com/apache/ozone/tree/master/.github/workflows) of the main Ozone repository.

The image is available as [apache/ozone-build](https://hub.docker.com/r/apache/ozone-build). Build is managed by Docker Hub.

## Development

To build the image, please use:

```
docker build -t apache/ozone-build:dev .
```

To test it, you can test any build step inside the container:

```
docker -it -v `pwd`:/opt/ozone` bash
cd /opt/ozone
mvn clean install -DskipTests
```

Note: the image assumes that the Ozone source tree (`pwd` in our example) is writted by the user with id=1000.


*After merging PR, a new tag can be pushed to the repository to create a new image. Use the convention: `YYYYMMDD-N` for tags where N is a daily counter (see the existing tags as an example).

