# gamingos-scripts

## Files

Hardware control:

- ./bin/hwctl
    - A Bash script to manage audio, battery, display, storage, and system information.

Resize root file system:

- ./lib/systemd/system/resize-root-file-system.service
    - A systemd service file to run the `resize-root-file-system.sh` script once and then disable itself so the service does not run again.
- ./bin/resize-root-file-system.sh
    - A script to resize the root file system to use all available space. Assumes the file system is Btrfs.

Swap creation:

- ./etc/sysctl.d/50-swappiness.conf
    - Lower the swappiness to 1.
- ./lib/systemd/system/create-swap.service
    - A systemd service file to run the `create-swap.sh` script once (after the `resize-root-file-system` service finishes) and then disable itself so the service does not run again.
- ./bin/create-swap.sh
    - A script to create swap if the RAM size is less than 32 GB.

## License

[GNU General Public License v3.0](LICENSE).
