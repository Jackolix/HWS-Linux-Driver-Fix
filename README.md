# HWS Linux Driver Fix

This repository contains fixes for the HWS Linux Driver to make it compatible with newer Linux kernel versions, specifically tested on Ubuntu 24.04.1 LTS with kernel 6.8.0-49-generic.

## Background

The original HWS Linux Driver (version 1.0.0.230324) has compatibility issues with newer Linux kernels due to:
1. Use of deprecated kernel functions
2. Reference to removed struct members

These fixes allow the driver to compile and work on modern Linux distributions.

## Issues Fixed

1. Replaced deprecated `strlcpy` function with `strscpy`
   - This function was removed in newer kernel versions
   - Affects string copying operations in the driver

2. Removed reference to `min_buffers_needed`
   - This field was removed from `struct vb2_queue`
   - Affects video buffer queue initialization

## Installation

1. Clone this repository:
```bash
git clone https://github.com/Jackolix/HWS-Linux-Driver-Fix.git
```

2. Navigate to the scripts directory:
```bash
cd HWS-Linux-Driver-Fix/scripts
```

3. Run the installation script:
```bash
sudo ./hws-ínstall.sh
```

## Original Driver Information

- Version: 1.0.0.230324
- Manufacturer Contact: alex.liu@longtimetech.com
- Original Installation Path: /usr/local/share/HWS

## System Requirements

- Ubuntu 24.04.1 LTS (tested)
- Kernel 6.8.0-49-generic (tested)
- May work with other modern Linux distributions and kernel versions

## Troubleshooting

If you encounter issues during installation:

1. Check the installation log:
```bash
cat hws_install.log
```

2. Ensure you have the required build tools:
```bash
sudo apt-get install make gcc dkms
```

3. Verify kernel headers are installed:
```bash
sudo apt-get install linux-headers-$(uname -r)
```

## Contributing

If you find additional issues or have improvements:

1. Fork the repository
2. Create a branch for your changes
3. Submit a pull request with a clear description of your modifications

## Disclaimer

These fixes are provided as-is to help users get the driver working on modern systems. This is not an official release from the original manufacturer. Use at your own risk.

## Contact

For issues with these fixes, please open an issue on GitHub.
For questions about the original driver, contact alex.liu@longtimetech.com
