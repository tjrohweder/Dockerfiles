FROM jenkinsci/blueocean

ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false"

RUN /usr/local/bin/install-plugins.sh ssh-slaves; \
    /usr/local/bin/install-plugins.sh mailer; \
    /usr/local/bin/install-plugins.sh kubernetes; \
    /usr/local/bin/install-plugins.sh blueocean-dashboard; \
    /usr/local/bin/install-plugins.sh workflow-multibranch; \
    /usr/local/bin/install-plugins.sh pipeline-stage-step; \
    /usr/local/bin/install-plugins.sh workflow-cps; \
    /usr/local/bin/install-plugins.sh pipeline-build-step; \
    /usr/local/bin/install-plugins.sh workflow-cps-global-lib; \
    /usr/local/bin/install-plugins.sh pipeline-stage-view; \
    /usr/local/bin/install-plugins.sh git; \
    /usr/local/bin/install-plugins.sh workflow-job