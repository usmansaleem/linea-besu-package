# Linea Besu Distribution

This project uses Gradle to manage dependencies, build tasks, and create distributions for linea-besu with all the necessary plugins to run a node for operators.
The build process is configured to download, extract, and copy various modules as specified in the `linea-besu/build.json` file. Additionally, it includes tasks for building Docker images.

## How-To Release

Releases are automated using GitHub Actions and are triggered by pushing a tag that matches the
pattern `'v[0-9]+.[0-9]+.[0-9]+`. (e.g., `v1.0.0`, `v2.1.3`)


### Create and Push a Tag

   Create a new tag that follows the pattern. Creating the tag will draft a release. This draft release will include the distribution artifact uploaded as an asset.
   ```sh
   git tag -a 'v0.0.1' 5cf01f9  -m 'Release test'
   git push origin v1.0.0
   ```

### Publish the release

   Once the draft release is published, the Docker image will also be created and published to registry.

## Update the Build Configuration

The build process is driven by the following configuration files:

- `linea-besu/build.json`: This file specifies the modules to be downloaded, extracted, or copied. Below is an example configuration:
- `gradle.properties`: This file provides additional properties used in the build process.

### Running the Build

To run the entire build process, including downloading, extracting, copying plugins, and creating distributions, you can execute:

```sh
gradle build
```

To build the Docker image, you can execute:

```sh
gradle distDocker
```

### Running with Docker

```sh
docker run -e BESU_PROFILE=follower-mainnet consensys/linea-besu-full:0.0.4-SNAPSHOT
```
