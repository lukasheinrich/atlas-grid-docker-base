FROM atlasadc/slc5
ENV HEP_OSLIBS_VER 1.0.3-0
LABEL maintainer="Alessandro.DeSalvo@roma1.infn.it"

# HEP OSLibs
RUN yum -y install http://linuxsoft.cern.ch/wlcg/sl5/x86_64/HEP_OSlibs_SL5-${HEP_OSLIBS_VER}.x86_64.rpm

# Final update and creation of the package list
RUN yum -y update
RUN rpm -qa > /var/lib/package-list

# Remove unuseful stuff
RUN rm -fr /var/lib/yum/* /var/cache/yum/* /usr/share/doc/* /boot/*

# Timestamp
RUN /bin/sh -c 'TS=`date +%Y%m%d%H%M%S`; echo $TS > /docker-creation-date'
RUN /bin/sh -c 'echo "export CDATE_DOCKER=\"`cat /docker-creation-date`\"" > /etc/profile.d/container-date.sh'
RUN /bin/sh -c 'echo "setenv CDATE_DOCKER \"`cat /docker-creation-date`\"" > /etc/profile.d/container-date.csh'

# Create site dirs
RUN mkdir -p /scratch /gpfs/work /gpfs/scratch /cvmfs /etc/grid-security/certificates /var/lib/condor /atlashome /srv /alrb
