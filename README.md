# Install NVIDA GRID or CUDA drivers

Install NVIDIA GRID or CUDA drivers.

- Install X11
- Install NVIDIA graphics drivers
- (optional) Install nvidia-container

## Requirements

Provisioning host:

- Ansible 2.15

Remote host:

- Ubuntu 22.04
- NVIDIA GPU
- docker (if installing nvidia-container)

## Example playbook

```yaml
- hosts: myhost
  roles:
    - name: xronos_nvidia_drivers_ansible
      role: xronos_nvidia_drivers_ansible
```

## Variables

- `nvidia_use_grid_drivers` (= `true`): Install Amazon-provided NVIDIA GRID drivers from s3. When false, NVIDIA CUDA repository drivers are used instead.
- `nvidia_grid_version` (see `defaults/main.yml` for default): Version of NVIDIA GRID driver to install. No effect if `nvidia_use_grid_drivers` is false.
- `nvidia_install_container` (= `true`): Install nvidia-container.
