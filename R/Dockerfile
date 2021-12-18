FROM r-base:latest

RUN apt-get update && \
    apt-get install -y libssl-dev libcurl4-openssl-dev libxml2-dev && \
    rm -rf /var/lib/apt/lists/*

RUN R -e "install.packages(c('oysteR', 'devtools'), dependencies=TRUE)"

# Install package with vulnerability
# https://ossindex.sonatype.org/component/pkg:cran/widgetframe
RUN R -e "require(devtools); install_version('widgetframe', version = '0.3.0')"
