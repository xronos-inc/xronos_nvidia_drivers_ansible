# Install NVIDA GRID or CUDA drivers

Install NVIDIA GRID or CUDA drivers.

- Install X11
- Install NVIDIA graphics drivers
- (optional) Install nvidia-container

## Requirements

Provisioning host:

- Ansible 2.15

Remote host:

- Ubuntu 22.04 or 24.04
- NVIDIA GPU
- docker (if installing nvidia-container)
- aws cli (GRID driver only)

## Example playbook

```yaml
- hosts: myhost
  roles:
    - name: xronos_nvidia_drivers_ansible
      role: xronos_nvidia_drivers_ansible
```

## Variables

- `nvidia_driver_install`: Install NVIDIA drivers. Defaults to `true`.
- `nvidia_driver_type`: Driver installation type. Defaults to `cuda`. Applies only when `nvidia_driver_install` is true.Valid options are:
  - `cuda`: install cuda drivers from NVIDIA repository.
  - `grid`: install NVIDIA GRID drivers from Amazon S3 repository. Requires AWS CLI is installed on the remote host.
  - `tesla`: install NVIDIA Tesla drivers from NVIDIA repository.
  - `open`: install NVIDIA open driver from Ubuntu repositories.
- `nvidia_unintall_driver`: Uninstall nvidia driver. May be combined with `nvidia_driver_install` to reinstall drivers. Uses versions numbers to uninstall specific versions. Defaults to `false`.
- `nvidia_install_container`: Install nvidia-container-toolkit. Defaults to `false`.

Additional variables when `nvidia_driver_type` is `cuda`:
- `nvidia_cuda_release`: Version of NVIDIA cuda driver to install. See `defaults/main.yml` for the default version.

Additional variables when `nvidia_driver_type` is `grid`:
- `nvidia_grid_release`: Version of NVIDIA GRID driver to install. See `defaults/main.yml` for the default version.

Additional variables when `nvidia_driver_type` is `tesla`:
- `nvidia_tesla_release`: Version of NVIDIA Tesla driver to install. See `defaults/main.yml` for the default version.

Additional variabels when `nvidia_driver_type` is `open`:
- `nvidia_ubuntu_release`: Version of NVIDIA open driver to install. See `defaults/main.yml` for the default version.

## Completely uninstall drivers

```yaml
- hosts: myhost
  roles:
    - name: xronos_nvidia_drivers_ansible
      role: xronos_nvidia_drivers_ansible
      vars:
        nvidia_uninstall_driver: true
        nvidia_install_driver: false
```
