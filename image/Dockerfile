FROM phpdoc/phpdoc:latest

ARG PHPDOC_FOLDER_PROJECT
ENV PHPDOC_FOLDER_PROJECT=${PHPDOC_FOLDER_PROJECT:-"/usr/local/apache2/www/"}
ARG PHPDOC_FOLDER_DOC
ENV PHPDOC_FOLDER_DOC=${PHPDOC_FOLDER_DOC:-"/usr/local/apache2/docs/"}
ENV PHPDOC_FOLDER_LOG="/var/log/docker/phpdoc/"
ENV PHPDOC_FOLDER_TMP="/var/tmp/docker/phpdoc/"
ENV PHPDOC_FOLDER_INI="/var/docker/phpdoc/"

RUN mv /opt/phpdoc/bin/phpdoc /opt/phpdoc/bin/phpdoc_def

RUN echo '#!/bin/bash' > /usr/bin/phpdoc
RUN echo '/opt/phpdoc/bin/phpdoc_def' >> /usr/bin/phpdoc
RUN chmod 777 /usr/bin/phpdoc

RUN mkdir -p ${PHPDOC_FOLDER_PROJECT}
RUN mkdir -p ${PHPDOC_FOLDER_DOC}
RUN mkdir -p ${PHPDOC_FOLDER_LOG}
RUN mkdir -p ${PHPDOC_FOLDER_TMP}
RUN mkdir -p ${PHPDOC_FOLDER_INI}

RUN echo '#!/bin/bash' > /opt/phpdoc/bin/phpdoc
RUN echo 'exec "$@"' >> /opt/phpdoc/bin/phpdoc
RUN chmod 777 /opt/phpdoc/bin/phpdoc

COPY phpdoc.xml ${PHPDOC_FOLDER_INI}/

#RUN echo '#!/bin/bash' > /usr/local/bin/shell.sh
#RUN echo '/bin/bash' >> /usr/local/bin/shell.sh

#RUN chmod 777 /usr/local/bin/shell.sh

WORKDIR ${PHPDOC_FOLDER_INI}

#CMD /usr/local/bin/shell.sh ; sleep infinity
CMD /bin/bash ; sleep infinity
#CMD ; sleep infinity