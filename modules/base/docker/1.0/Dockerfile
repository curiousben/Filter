####################################
# Core Filter Image
# Author: BenSmith(CuriousBen)
####################################

FROM curiousben/redismq-nodejs-amd:latest
#----INFO: Labeling the image
LABEL version=${NPM_PACKAGE_VERSION} \
      maintainer="benjamindsmith3@gmail.com"

#----INFO:Update package indices with the udate to date source and installing basic utilities
RUN apk update --no-cache 

#----INFO:Coping local tarball of RedisMQ client
ARG NPM_PACKAGE
ADD .${PACKAGE_PATH}/${NPM_PACKAGE} /tmp
#----INFO:Installing the npm package for production globally
RUN npm install /tmp/${NPM_PACKAGE} --production --global \

#----INFO:INFO: Linking the RedisMQ library so any program can use it
  && npm link filter \

#----INFO:Remove the tarball of RedisMQ
  && rm /tmp/${NPM_PACKAGE} \

#----INFO: Verifies that the npm cache is indexed properly and collects any garbage
  && npm cache verify
