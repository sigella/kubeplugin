#!/bin/bash

# help message
HELP_MESSAGE=$(cat <<EOF
echo "Usage: $0 <resource_type (pods|nodes)> <namespace>"
echo "Examples:"
  echo "./$0 pods kube-system"
  echo "./$0 pods"
  echo "./$0 nodes"
EOF
)

# Assign variables
RESOURCE_TYPE=$1
NAMESPACE=$2

# Check arguments
if [ "$#" -lt 1 ] || [ "$#" -ge 3 ] || [ "$1" == "-h" ] || [ "$1" == "--help" ]; then
  echo "${HELP_MESSAGE}"
  exit 1
fi

if [ "${RESOURCE_TYPE}" != "pods" ] && [ "${RESOURCE_TYPE}" != "nodes" ]; then
  echo "${HELP_MESSAGE}"
  exit 1
fi

echo "Resource, Namespace, Name, CPU, Memory"

# Get resource usage and process
kubectl top $RESOURCE_TYPE -n "$NAMESPACE" | tail -n +2 | while read -r line
do
  NAME=$(echo "$line" | awk '{print $1}')
  CPU=$(echo "$line" | awk '{print $2}')
  MEMORY=$(echo "$line" | awk '{print $3}')
  
  # Print CSV header
  echo "$RESOURCE_TYPE, $NAMESPACE, $NAME, $CPU, $MEMORY"
done
