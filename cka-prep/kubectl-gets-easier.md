## Make `kubectl` Easier to Use

### Enable Bash completion

```bash
source <(kubectl completion bash)
echo 'source <(kubectl completion bash)' >> ~/.bashrc
```

### Create the ```k``` alias
```bash
alias k=kubectl
echo 'alias k=kubectl' >> ~/.bashrc
```

### Enable completion for ```k```
```bash
complete -o default -F __start_kubectl k
echo 'complete -o default -F __start_kubectl k' >> ~/.bashrc
```

### Reload Bash configuration
```bash
source ~/.bashrc
```