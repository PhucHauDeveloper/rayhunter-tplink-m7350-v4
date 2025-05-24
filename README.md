![Rayhunter Logo - An Orca taking a bite out of a cellular signal bar](https://www.eff.org/files/styles/media_browser_preview/public/banner_library/rayhunter-banner.png)

# Rayhunter for TP-Link M7350 V4

![Tests](https://github.com/EFForg/rayhunter/actions/workflows/check-and-test.yml/badge.svg)

Rayhunter is an IMSI Catcher Catcher originally developed for the Orbic mobile hotspot (US market) and now ported to the TP-Link M7350 mobile hotspot (available worldwide).

**THIS CODE IS PROOF OF CONCEPT, IS BEING ACTIVELY DEVELOPED AND SHOULD NOT BE RELIED UPON IN HIGH RISK SITUATIONS**

## The Hardware

TP-Link M7350 mobile hotspot has several hardware revisions. You can check your version on a sticker behind the battery. Rayhunter has been tested and confirmed working on multiple versions of the TP-Link M7350.

## Installing Rayhunter

You can install Rayhunter easily by downloading and running the installation script.

### Quick Setup

1. Download the latest release from the [Releases Page](PhucHauDeveloper/rayhunter-tplink-m7350-v4/releases).
2. Extract the archive.
3. Open the extracted folder.
4. Run the `install.cmd` (Windows).
5. Follow the on-screen instructions.

After installation, the device will reboot and launch Rayhunter automatically. No manual telnet setup or firmware downgrades are required.

You can now access Rayhunter's Web UI at:

* `http://192.168.0.1:8080`

### 🚀 What's New in This Fork

This customized fork brings several usability and performance improvements over the original Rayhunter version:

    ✅ Web UI Integrated Directly into the TP-Link Admin Page
    You can access Rayhunter controls directly from the TP-Link web interface at http://192.168.0.1, no separate port or web UI required.

    ✅ Physical Button to Toggle Rayhunter
    Press and hold the top button on your TP-Link M7350 for 3 seconds to quickly enable or disable Rayhunter without needing a web or shell interface.

    ✅ Live Status Indicator on LCD Screen
    After the carrier name, if you see a #: symbol, Rayhunter is active. If this symbol is missing, Rayhunter is inactive.

    ✅ SSH Enabled, Telnet Disabled After Installation
    For better security, SSH is enabled by default for remote access, while Telnet is automatically disabled once the installation is complete.

    ✅ Built-in TTL Modification Tool (ttlset)
    This fork includes ttlset, allowing you to modify TTL values easily—useful for bypassing carrier tethering detection.

📌 These enhancements are designed to improve user experience and security while keeping installation simple and accessible.
## Usage

<img src="https://github.com/user-attachments/assets/03f78f43-53f9-44de-a122-2dd01dddc369" width=250>

Once installed, Rayhunter will run automatically. It serves a web UI that provides basic controls, such as:

* Starting/stopping recordings
* Downloading captures
* Viewing heuristic analyses of captures

You can access the UI in one of two ways:

1. **Over WiFi**: Connect your phone/laptop to the TP-Link M7350 WiFi network and visit `http://192.168.0.1:8080`
2. **Over USB**: Connect the device via USB and visit the same address.

**Note:** If you are using VPN, you may not be able to access the UI.

If Rayhunter detects something, it will highlight it in the UI with a red line and logs:

<img src="https://github.com/user-attachments/assets/4202d40c-0f7b-4ac4-a1a5-39e02b45de51" width=250>

<img src="https://github.com/user-attachments/assets/96e559c9-3ec7-4fdd-af19-5a2ebd16a0fb" width=250>

## Frequently Asked Questions

### Do I need an active SIM card?

**Optional.** Some functionality may require a SIM card, but not necessarily an active one. You are encouraged to test with or without and share findings with the Rayhunter team.

### What if Rayhunter detects something?

You may consider turning off your phone or switching to airplane mode if suspicious activity is detected. Please share your data with [EFF](mailto:info@eff.org) (securely, if needed).

### Does Rayhunter work outside the US/Europe?

Yes. TP-Link M7350 is compatible with many LTE bands in Europe and Asia, and should work in most parts of Africa and South America.

## Development (compiling Rayhunter binary)

Install dependencies:

```bash
sudo apt install curl build-essential libc6-armhf-cross libc6-dev-armhf-cross gcc-arm-linux-gnueabihf rustup cargo
rustup default stable
rustup target add x86_64-unknown-linux-gnu
rustup target add armv7-unknown-linux-gnueabihf
```

Clone and build:

```bash
git clone https://github.com/EFForg/rayhunter
cd rayhunter
cargo build --target armv7-unknown-linux-gnueabihf --release
```

Binaries are located in:

```
target/armv7-unknown-linux-gnueabihf/release/
```

Generate documentation:

```bash
RUSTDOCFLAGS="--cfg docsrs" cargo doc --no-deps --all-features --open
```

## LEGAL DISCLAIMER

Use at your own risk. Rayhunter does **not** intercept third-party traffic or modify baseband firmware. It uses Qualcomm DIAG to access **your own device's** diagnostic info.

That said, please verify legality in your own jurisdiction. The authors disclaim responsibility for misuse or liability.

*Good Hunting!*
