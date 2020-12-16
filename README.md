# Natural Resources Common Services Showcase DevOps Tools [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE) [![img](https://img.shields.io/badge/Lifecycle-Stable-97ca00)](https://github.com/bcgov/repomountie/blob/master/doc/lifecycle-badges.md)

This repository is for the NR Common Services Showcase Devops tools.  This includes our Continuous Integration / Continuous Delivery (CICD) setup used in other projects.  The tools are used to create a full Pull Request based CICD pipeline.  This is continually evolving as more tools are added (ex. Sonarqube) to our pipeline. This repository also contains potentially useful standalone tools (ex. Metabase) that may be needed in certain contexts.

## Directory Structure

    .github/                   - PR and Issue templates
    tools/                     - Devops utilities
    ├── jenkins                - Jenkins standup
    └── metabase               - Metabase standup
    CODE-OF-CONDUCT.md         - Code of Conduct
    CONTRIBUTING.md            - Contributing Guidelines
    LICENSE                    - License

## Documentation

* [Installation](tools/README.md)
* [Showcase Team Roadmap](https://github.com/bcgov/nr-get-token/wiki/Product-Roadmap)
* [Devops Tools SonarQube Demo app](https://github.com/bcgov/nr-showcase-devops-tools-demo-sq.git)
* [Metabase Installation](tools/metabase/README.md)

## Getting Help or Reporting an Issue

To report bugs/issues/features requests, please file an [issue](https://github.com/bcgov/nr-showcase-devops-tools/issues).

## How to Contribute

If you would like to contribute, please see our [contributing](CONTRIBUTING.md) guidelines.

Please note that this project is released with a [Contributor Code of Conduct](CODE-OF-CONDUCT.md). By participating in this project you agree to abide by its terms.

## License

    Copyright 2019 Province of British Columbia

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
