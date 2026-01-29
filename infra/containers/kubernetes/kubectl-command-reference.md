# Kubectl Command Reference

## Context & Configuration

```bash
# View current context
k config current-context

# List contexts
k config get-contexts

# Switch context
k config use-context <context>

# Set default namespace
k config set-context --current --namespace=<namespace>
```

## Viewing Resources

```bash
# Get resources
k get pods
k get pods -o wide                 # More details
k get pods -A                      # All namespaces
k get pods -n <namespace>          # Specific namespace
k get pods -w                      # Watch for changes

# Common resource types
k get nodes
k get deployments
k get services
k get configmaps
k get secrets
k get ingress
k get pv                           # Persistent volumes
k get pvc                          # Persistent volume claims

# Get all resources
k get all

# Describe resource (detailed info)
k describe pod <name>
k describe node <name>

# Output formats
k get pods -o yaml
k get pods -o json
k get pods -o jsonpath='{.items[*].metadata.name}'
```

## Creating & Applying Resources

```bash
# Apply from file
k apply -f <file.yaml>
k apply -f <directory>/
k apply -f <url>

# Create resource imperatively
k create deployment <name> --image=<image>
k create namespace <name>
k create configmap <name> --from-literal=key=value
k create secret generic <name> --from-literal=key=value

# Expose deployment as service
k expose deployment <name> --port=80 --target-port=8080
```

## Editing & Updating

```bash
# Edit resource
k edit deployment <name>

# Set image
k set image deployment/<name> <container>=<image>:<tag>

# Scale deployment
k scale deployment <name> --replicas=3

# Rollout management
k rollout status deployment/<name>
k rollout history deployment/<name>
k rollout undo deployment/<name>
k rollout restart deployment/<name>
```

## Deleting Resources

```bash
# Delete resource
k delete pod <name>
k delete -f <file.yaml>

# Delete all pods in namespace
k delete pods --all -n <namespace>

# Force delete stuck pod
k delete pod <name> --force --grace-period=0
```

## Debugging & Logs

```bash
# View logs
k logs <pod>
k logs <pod> -c <container>        # Specific container
k logs <pod> -f                    # Follow logs
k logs <pod> --tail=100            # Last 100 lines
k logs <pod> --previous            # Previous instance

# Execute command in pod
k exec <pod> -- <command>
k exec -it <pod> -- /bin/bash      # Interactive shell
k exec -it <pod> -c <container> -- /bin/bash

# Port forwarding
k port-forward pod/<pod> 8080:80
k port-forward svc/<service> 8080:80

# Copy files
k cp <pod>:/path /local/path
k cp /local/path <pod>:/path

# Debug node
k debug node/<node> -it --image=ubuntu
```

## Resource Management

```bash
# View resource usage
k top nodes
k top pods

# Get events
k get events
k get events --sort-by='.lastTimestamp'

# Dry run (test without applying)
k apply -f file.yaml --dry-run=client
k apply -f file.yaml --dry-run=server
```

## Labels & Selectors

```bash
# Add label
k label pod <name> key=value

# Remove label
k label pod <name> key-

# Select by label
k get pods -l app=nginx
k get pods -l 'app in (nginx,apache)'
```

## Namespaces

```bash
# List namespaces
k get namespaces

# Create namespace
k create namespace <name>

# Delete namespace
k delete namespace <name>
```

