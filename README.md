WORKBENCH_NAME="sudo-workbench-test-008"
NAMESPACE="demoproject"
oc adm policy add-scc-to-user privileged -z ${WORKBENCH_NAME} -n ${NAMESPACE}
oc patch notebook ${WORKBENCH_NAME} --type=merge -n ${NAMESPACE} -p "{\"spec\":{\"template\":{\"spec\":{\"containers\":[{\"name\":\"${WORKBENCH_NAME}\",\"securityContext\":{\"privileged\":true}}]}}}}"

oc patch notebook ${WORKBENCH_NAME} --type=merge -n ${NAMESPACE} -p "{\"spec\":{\"template\":{\"spec\":{\"containers\":[{\"name\":\"${WORKBENCH_NAME}\", \"securityContext\":{\"privileged\":true}}]}}}}"
