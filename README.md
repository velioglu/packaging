# Citus Packaging

A set of scripts that generate a set of Dockerfiles that generate a set of Docker images which generate PostgreSQL 9.4/9.5-compatible builds of Citus on many platforms.

## Usage

Unless you have a reason to change the Dockerfiles, just use the images hosted on Docker Hub. They’ll be pulled automatically as they’re needed. To build all packages, run the `build_packages.sh` script from the project root. Output will be put in OS/release-specific subdirectories of a `packages` directory in the project root.

### Config

Until the Citus repo is public, you’ll need a `GITHUB_TOKEN` environment variable set to a GitHub OAuth token to permit downloads of private repos.

The list of supported OSes comes from `os-list.csv`.

### Updating Dockerfiles

`update_dockerfiles.sh` builds a new set of Dockerfiles (under the `dockerfiles` directory in the project root) based on combining `os-list.csv` with the templates in the `templates` directory. Debian builds use `pg_buildext` to build Citus for all extensions at once, but Red Hat-based OSes have separate `base`, `94`, and `95` images to facilitate building 9.4- and 9.5-compatible extensions in containers specific to those PostgreSQL releases.

### Updating Docker Images

`update_images.sh` will regenerate all Docker images based on the Dockerfiles generated by `update_dockerfiles.sh`. This is only necessary if you wish to make a fix to an existing image and plan to push it to Docker Hub; otherwise, just use the Docker Hub images.

## License

The following license information (and associated [LICENSE][license] file) apply _only to the files within **this** repository_. Please consult Citus’s own repository for information regarding its licensing.

Copyright © 2016 Citus Data, Inc.

Licensed under the Apache License, Version 2.0 (the “License”); you may not use this file except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an “AS IS” BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
