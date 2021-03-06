FROM bitnami/minideb-extras:stretch-r130
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    HOME="/"

# Install required system packages and dependencies
RUN install_packages libblkid1 libbsd0 libbz2-1.0 libc6 libffi6 libgcc1 libglib2.0-0 libjemalloc1 libmount1 libncurses5 libpcre3 libreadline7 libselinux1 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 libuuid1 libx11-6 libxau6 libxcb1 libxdmcp6 libxext6 zlib1g
RUN bitnami-pkg install python-2.7.15-2 --checksum 1d5e9d3a2f7225d159913e3a8792577057abc0ceba7c7d60299bb8d59933258c
RUN bitnami-pkg install java-1.8.181-1 --checksum 66bba4b4a2647f981339d306da796905c222057c4277a5ef045e079981a404f4
RUN bitnami-pkg unpack cassandra-3.11.3-7 --checksum 75638bbb702acc9f25cbdc6376d1b85610e910e59387b9d09d6546aba6c96c43

COPY rootfs /
ENV BITNAMI_APP_NAME="cassandra" \
    BITNAMI_IMAGE_VERSION="3.11.3-debian-9-r39" \
    CASSANDRA_CLUSTER_NAME="My Cluster" \
    CASSANDRA_CQL_PORT_NUMBER="9042" \
    CASSANDRA_ENABLE_REMOTE_CONNECTIONS="true" \
    CASSANDRA_ENDPOINT_SNITCH="SimpleSnitch" \
    CASSANDRA_HOST="" \
    CASSANDRA_JMX_PORT_NUMBER="7199" \
    CASSANDRA_NUM_TOKENS="256" \
    CASSANDRA_PASSWORD="cassandra" \
    CASSANDRA_PASSWORD_SEEDER="no" \
    CASSANDRA_SEEDS="" \
    CASSANDRA_STARTUP_CQL="" \
    CASSANDRA_TRANSPORT_PORT_NUMBER="7000" \
    CASSANDRA_USER="cassandra" \
    PATH="/opt/bitnami/python/bin:/opt/bitnami/java/bin:/opt/bitnami/cassandra/bin:$PATH"

EXPOSE 9042 7000

USER 1001
ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "cassandra" ]
