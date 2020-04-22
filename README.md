# ISLE 8 - isle-fcrepo-base image

## Assumptions

To be used with:

* Docker-compose service
* ISLE 8 Mariadb for the database
* ActiveMQ as the JMS broker
* ISLE 8 isle-fcrepo image / container for Islandora specific edits e.g. SYN etc.
* The Drupal 8 site

* This base image is temporary until an official image from the Fedora Commons community is created.
  * Additionally, this base image has no specific Islandora configurations and is meant to solely run `fcrepo`

* `namespaces.cnd` is used as a sample from a merge of:
  * https://wiki.lyrasis.org/display/FEDORA51/Best+Practices+-+RDF+Namespaces
  * https://wiki.lyrasis.org/display/FEDORA475/Best+Practices+-+RDF+Namespaces

---

## Specifications

* Uses official Tomcat image: [tomcat:8.5-jdk8](https://github.com/docker-library/tomcat/blob/200fb67e66016f412b5e8428e48e7794dd7faae7/8.5/jdk8/openjdk/Dockerfile)

**Contains**:

* [Fedora](https://github.com/fcrepo4/fcrepo4/releases/tag/fcrepo-5.1.0) `5.1.0`
* [Tomcat](https://tomcat.apache.org/download-80.cgi)`8.5.x`
* [OpenJDK](https://openjdk.java.net/) `8`
  * Versions 11 & 13 on with Tomcat 9 fail using Fedora 5.
  * TBD fixes and testing from Fedora community, using Tomcat 8 & OpenJDK 8 to match [Islandora Playbook](https://github.com/Islandora-Devops/islandora-playbook) versions
* Ability to configure modeshape within the ISLE 8 project `fedora.env`

**Does not contain**:

* A Tomcat admin panel nor a root war. Please use the `isle-fcrepo` image to get these items

* Instructions on how to run separate from the `isle-fcrepo` image.

---

## MVP 3 sprint

### Building

In order to build locally, run this command

* `docker build -t borndigital/isle-fcrepo-base:mvp3-alpha .`

### Docker-Hub

Born-Digital is currently supplying pre-built images from their Docker Hub registry. This image and others are currently used in the `isle-dc` docker-compose.yml until the official Islandora Dockerhub account becomes available.

You can pull this image e.g. `docker pull borndigital/isle-fcrepo-base:mvp3-alpha` or performing `docker-compose pull` from within a local `isle-dc` project directory.

### Testing

To test Fedora...
