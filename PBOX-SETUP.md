# PBOX Pereval

This branch adapts the original Pereval project for a test Ubuntu 24.04 VDS.

- Host: box-988502
- IPv4: 170.168.107.36
- Domain: dns.pbox-bk.ru
- Metadata and supported services: services.yaml
- Current installed software: AdGuard Home and Nginx. This branch has not been deployed.

## Build check

```bash
sudo apt install -y python3 python3-yaml
python3 generate.py services.yaml 170.168.107.36 --check
python3 generate.py services.yaml 170.168.107.36 --out-dir /tmp/pbox-generated
```

The original deploy.sh is not yet tailored for the current server. Back up the existing configuration before deployment. Do not enable automatic GitHub Actions deployment until the migration has been tested.
