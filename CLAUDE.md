# CLAUDE.md

## Project Overview

This repository contains a Python tool designed to retrieve RADIUS server certificates from WPA2/WPA3 Enterprise wireless networks. This is particularly useful for configuring secure enterprise WiFi connections on various devices.

## Purpose

When connecting to WPA2/WPA3 Enterprise networks (commonly found in corporate, university, and institutional environments), the network uses 802.1X authentication with a RADIUS server. This authentication process involves certificate-based encryption to secure the communication channel.

Many devices and operating systems require the RADIUS server's certificate to be manually configured for proper validation and secure connection. This tool automates the process of retrieving that certificate.

## WPA2/WPA3 Enterprise Background

### What is WPA2/WPA3 Enterprise?

- **WPA2/WPA3 Enterprise** uses 802.1X authentication protocol
- Authentication is handled by a **RADIUS** (Remote Authentication Dial-In User Service) server
- Provides per-user credentials instead of a shared network password
- Uses various EAP (Extensible Authentication Protocol) methods like:
  - EAP-TLS (certificate-based)
  - EAP-TTLS (tunneled TLS)
  - PEAP (Protected EAP)

### Why Do You Need the Certificate?

1. **Certificate Validation**: Ensures you're connecting to the legitimate RADIUS server
2. **Security**: Prevents man-in-the-middle attacks
3. **Device Configuration**: Many devices require the certificate to be installed before connecting
4. **Trust Establishment**: Validates the identity of the authentication server

## Use Cases

- Setting up enterprise WiFi on mobile devices (iOS, Android)
- Configuring Linux systems for institutional networks
- Network security auditing (with proper authorization)
- Educational purposes to understand 802.1X authentication
- Troubleshooting enterprise wireless connectivity issues

## Technical Details

The tool uses:
- **scapy**: For network packet manipulation and capture
- **ssl**: For certificate extraction and handling

## Requirements

- Python 3.x
- Dependencies listed in `requirements.txt`:
  - scapy
  - ssl (standard library)

## Installation

```bash
pip install -r requirements.txt
```

## Important Notes

### Security and Authorization

- Only use this tool on networks you own or have explicit authorization to test
- This is intended for legitimate network configuration and authorized security testing
- Unauthorized access to network infrastructure may violate local laws and regulations

### Typical Workflow

1. Run the tool to capture the RADIUS server certificate
2. Save the certificate to a file
3. Import the certificate into your device's trusted certificate store
4. Configure your WiFi connection with the appropriate EAP method and credentials
5. Connect to the enterprise network with proper certificate validation

## Common Enterprise WiFi Configuration

Once you have the certificate:

1. **Import Certificate**: Install the retrieved certificate on your device
2. **Configure WiFi Settings**:
   - SSID: Your network name
   - Security: WPA2/WPA3 Enterprise
   - EAP Method: (PEAP, TTLS, TLS, etc.)
   - Phase 2 Auth: (MSCHAPv2, PAP, etc.)
   - CA Certificate: The certificate obtained from this tool
   - Identity: Your username
   - Password: Your password

## Contributing

Contributions are welcome! Please ensure any additions maintain the security-focused and educational nature of this tool.

## License

See LICENSE file for details.
