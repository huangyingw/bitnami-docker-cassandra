FROM bitnami/minideb-extras:stretch-r70
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages libblkid1 libbsd0 libbz2-1.0 libc6 libffi6 libgcc1 libglib2.0-0 libjemalloc1 libmount1 libncurses5 libpcre3 libreadline7 libselinux1 libsqlite3-0 libssl1.1 libstdc++6 libtinfo5 libuuid1 libx11-6 libxau6 libxcb1 libxdmcp6 libxext6 zlib1g
RUN bitnami-pkg install python-2.7.15-1 --checksum ffca53ea1dc9e9f582b1c5bab492df739461e58a9b7c3753180fb8bfcca7630d
RUN bitnami-pkg install java-1.8.171-3 --checksum 100e1e457e19648410be57716eb075f43936aeaa2ac51457d2b46abc2b810ddc
RUN bitnami-pkg unpack cassandra-3.11.2-4 --checksum bbf01be7b104436382bd89882a74d440147678fb9466cd35307ba92636f5651b

COPY rootfs /
ENV BITNAMI_APP_NAME="cassandra" \
    BITNAMI_IMAGE_VERSION="3.11.2-debian-9-r2" \
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
    CASSANDRA_TRANSPORT_PORT_NUMBER="7000" \
    CASSANDRA_USER="cassandra" \
    PATH="/opt/bitnami/python/bin:/opt/bitnami/java/bin:/opt/bitnami/cassandra/bin:$PATH"

EXPOSE 9042 7000

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","cassandra"]