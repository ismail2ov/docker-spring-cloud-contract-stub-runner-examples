FROM ismail2ov/spring-cloud-contract-stub-runner:1.0.0

LABEL Author="Ismail Ahmedov <i.a.ismailov@gmail.com>"

WORKDIR /home/scc

ENV STUBS_GROUP_ID es.devex
ENV STUBS_ARTIFACT_ID catalog
ENV STUBS_VERSION 0.0.1-SNAPSHOT
ENV STUBS_FOLDER es/devex

ENV REPOSITORY_FOLDER .m2/repository/${STUBS_FOLDER}/${STUBS_ARTIFACT_ID}/${STUBS_VERSION}/

ENV STUBRUNNER_IDS ${STUBS_GROUP_ID}:${STUBS_ARTIFACT_ID}:${STUBS_VERSION}:stubs:${STUBRUNNER_PORT}

VOLUME /tmp

RUN mkdir -p ${REPOSITORY_FOLDER}
COPY --chown=scc:scc ./stubs/${STUBS_ARTIFACT_ID}-${STUBS_VERSION}-stubs.jar ${REPOSITORY_FOLDER}

RUN echo "Fetching dependencies, please wait..."
RUN java -Dthin.dryrun=true -jar stub-runner-boot.jar

ENTRYPOINT ["./run.sh"]