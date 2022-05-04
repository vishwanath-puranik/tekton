ARG  FROMIMAGE=quay.io/vishwanath_puranik/ace-server:latest
FROM ${FROMIMAGE}

USER root

COPY /workspace/tekton/*.bar /tmp
RUN export LICENSE=accept \
    && . /opt/ibm/ace-12/server/bin/mqsiprofile \
    && set -x && for FILE in /tmp/*.bar; do ibmint deploy --input-bar-file "$FILE" --output-work-directory /home/aceuser/ace-server/ 2>&1 >  /tmp/deploys; done \
    && chmod -R ugo+rwx /home/aceuser/

