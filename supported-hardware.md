# Supported Hardware Configurations

## Supported Graphics Card
Sunshine supports Windows and Linux Host Operating Systems.

On Linux any graphics card should work fine.

On Windows a graphics card that has DirectX11 Support is mandatory, and a display (or an HDMI Dummy Plug) must be connected


| GPU Vendor               | Windows     | Linux       |
|--------------------------|-------------|-------------|
| Nvidia (Proprietary)     | Yes (NVEnc) | Yes (NVEnc)*        |
| Nvidia (Noveau Drivers   | N/A         | Yes (VAAPI) |
| AMD                      | Yes (AMF)   | Yes (VAAPI) |
| Intel                    | No          | No**        |

\* Uses some CPU code for encoding<br>
** Flaky support for Intel GPU Drivers by VAAPI

**NOTE:** NVdia optimus (Laptop with both an integrated and dedicated graphics card) do not always work correctly.