<img src="doc/logo.svg">

---

# GitGuardian Shield Circle CI Orb

Find exposed credentials in your commits.

## Installation

To add gg-shield to your pipelines configure your `.circleci/config.yml` to add the gg-shield orb:

```yaml
orbs:
  gg-shield: gitguardian/gg-shield

workflows:
  main:
    jobs:
      - gg-shield/scan:
          name: gg-shield-scan # best practice is to name each orb job
          base_revision: << pipeline.git.base_revision >>
          revision: <<pipeline.git.revision>>
```

Do not forget to add your [GitGuardian API Key](https://dashboard.gitguardian.com/api/v1/auth/user/github_login/authorize?utm_source=github&utm_medium=gg_shield&utm_campaign=shield1) to the `GITGUARDIAN_API_KEY` environment variable in your project settings.

## License

This project is licensed under the MIT License - read [LICENSE](LICENSE) file for details.
