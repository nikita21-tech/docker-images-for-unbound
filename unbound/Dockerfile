FROM centos:7

# Install unbound
RUN yum update -y && yum install epel-release unbound bind-utils vim  wget -y
RUN wget http://dns.measurement-factory.com/tools/dnstop/
RUN yum install dnstop -y


# Expose udp port
EXPOSE 53/udp
EXPOSE 53/tcp
WORKDIR /etc/unbound

COPY unbound.conf /etc/unbound/unbound.conf
RUN unbound-control-setup
COPY named.cache /etc/unbound/named.cache
COPY entrypoint.sh /sbin/entrypoint.sh
RUN chmod 755 /sbin/entrypoint.sh
RUN chmod 666 /etc/unbound/unbound.conf
ENTRYPOINT ["/sbin/entrypoint.sh"]


