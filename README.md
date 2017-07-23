# Silverstripe CircleCI Docs
Documentation on how to integrate a SilverStripe website with CircleCI 2.0, using the [brettt89/silverstripe-web](https://hub.docker.com/r/brettt89/silverstripe-web/) docker image.

### Assumptions:
- SilverStripe 4 website (this should work with SilverStripe 3+ sites).
- The project is in [Github](https://github.com/).
- You are an admin user for the project.
- You have access to [CircleCI](https://circleci.com/).

### Steps:
1. Login to CircleCI using your Github credentials.
2. Make sure the correct organization is selected through the organization selector (top left).
3. Add the project through the **Projects** section.
4. Select `Setup project` on the project you want to integrate with CircleCI:
  - Ensuring the correct respository is selected.
  - OS = Linux
  - Platform = 2.0
  - Language = PHP
5. Create a folder in the root of the project `.circleci` with a file `config.yml` containing the example config. (see `circleci/config.yml`)
6. Push this file to the repo.

### Notes:
- Default runs builds against `master`, `develop`, and `/feature.*/` branches, this can be modified under the `branches` section of the **config.yml**.
- Unit tests default to all tests defined in `phpunit.xml` in the root of your website. See [https://docs.silverstripe.org/en/4/developer_guides/testing/#running-tests](https://docs.silverstripe.org/en/4/developer_guides/testing/#running-tests) for running unit tests.

### Debugging:
CircleCI can be run locally, see [https://circleci.com/docs/2.0/local-jobs/](https://circleci.com/docs/2.0/local-jobs/).
- Requires [docker](https://docs.docker.com/engine/installation/) installed on the machine.
- To validate the config syntax: `$ circleci config validate -c .circleci/config.yml`
- To build and run the image locally: `$ circleci build`
- To use environment variables: see [https://circleci.com/docs/2.0/local-jobs/#environment-variables](https://circleci.com/docs/2.0/local-jobs/#environment-variables)
- For help run: `$ circleci help build`

### Links:
- https://circleci.com/docs/2.0/about-circleci/
- https://hub.docker.com/r/brettt89/silverstripe-web/
