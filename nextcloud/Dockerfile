FROM nextcloud:27.1.10

RUN apt update
# Install extra codecs to enable SVG support in web interface, see https://github.com/nextcloud/server/issues/24710
RUN apt install -qy libmagickcore-6.q16-6-extra