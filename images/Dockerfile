FROM registry.svc.ci.openshift.org/openshift/release:golang-1.13 AS builder
WORKDIR /go/src/github.com/openshift/openshift-apiserver
COPY . .
RUN make build --warn-undefined-variables

FROM registry.svc.ci.openshift.org/openshift/origin-v4.5:base
COPY --from=builder /go/src/github.com/openshift/openshift-apiserver/openshift-apiserver /usr/bin/
ENTRYPOINT ["/usr/bin/openshift-apiserver"]
LABEL io.k8s.display-name="OpenShift API Server Command" \
      io.k8s.description="OpenShift is a platform for developing, building, and deploying containerized applications." \
      io.openshift.tags="openshift,openshift-apiserver"
