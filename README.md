<a href="https://gitguardian.com/"><img src="https://cdn.jsdelivr.net/gh/GitGuardian/gg-shield-orb/doc/logo.svg"></a>

---

# [GitGuardian Shield](https://github.com/GitGuardian/gg-shield) Circle CI Orb

[![Circle CI Registry](https://img.shields.io/badge/CircleCI%20Registry-v1-undefined.svg?logo=circleci&logoColor=white&style=for-the-badge)](https://circleci.com/orbs/registry/orb/gitguardian/ggshield)
[![Docker Image Version (latest semver)](https://img.shields.io/docker/v/gitguardian/ggshield?color=1B2D55&sort=semver&style=for-the-badge&label=ggshield)](https://hub.docker.com/r/gitguardian/ggshield)
[![License](https://img.shields.io/github/license/GitGuardian/gg-shield-orb?color=%231B2D55&style=for-the-badge)](LICENSE)
![GitHub stars](https://img.shields.io/github/stars/gitguardian/gg-shield-orb?color=%231B2D55&style=for-the-badge)

Find exposed credentials in your commits using [**GitGuardian shield**](https://github.com/GitGuardian/gg-shield).

The **GitGuardian shield** (gg-shield) is a CLI application that runs in your local environment
or in a CI environment to help you detect more than 200 types of secrets, as well as other potential security vulnerabilities or policy breaks.

**GitGuardian shield** uses our [public API](https://api.gitguardian.com/doc) through [py-gitguardian](https://github.com/GitGuardian/py-gitguardian) to scan your files and detect potential secrets or issues in your code. **The `/v1/scan` endpoint of the [public API](https://api.gitguardian.com/doc) is stateless. We will not store any files you are sending or any secrets we have detected**.

You'll need an **API Key** from [GitGuardian](https://dashboard.gitguardian.com/api/v1/auth/user/github_login/authorize?utm_source=github&utm_medium=gg_shield&utm_campaign=shield1) to use gg-shield.

## Installation

To add GitGuardian shield to your pipelines configure your `.circleci/config.yml` to add the ggshield orb:

```yaml
version: 2.1

orbs:
  ggshield: gitguardian/ggshield@volatile

workflows:
  main:
    jobs:
      - ggshield/scan:
          name: ggshield-scan # best practice is to name each orb job
          base_revision: << pipeline.git.base_revision >>
          revision: <<pipeline.git.revision>>
```

Do not forget to add your [GitGuardian API Key](https://dashboard.gitguardian.com/api/v1/auth/user/github_login/authorize?utm_source=github&utm_medium=gg_shield&utm_campaign=shield1) to the `GITGUARDIAN_API_KEY` environment variable in your project settings.

## License

This project is licensed under the MIT License - read [LICENSE](LICENSE) file for details.
