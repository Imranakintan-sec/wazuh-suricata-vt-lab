# VirusTotal File Detection Investigation

## 1. Detection Summary

Wazuh detected a file created in the `/root` directory on the Ubuntu
16.04 endpoint and subsequently generated a VirusTotal alert for the
file.

- **Endpoint:** vtcsec
- **File:** `/root/eicar.com`
- **Initial Detection:** File added to `/root`
- **Wazuh FIM Rule:** 100201
- **VirusTotal Alert Rule:** 87105
- **VirusTotal Alert Severity:** Level 12

## 2. Investigation

The EICAR test file was introduced into the monitored `/root`
directory as a controlled malware-detection test.

Wazuh File Integrity Monitoring detected the creation of the file and
generated a file-added event.

The VirusTotal integration then provided threat-intelligence
enrichment for the detected file, resulting in a VirusTotal alert in
Wazuh.

## 3. Analysis

The EICAR file was identified through its file metadata and enriched
with VirusTotal threat-intelligence information.

The investigation evidence includes the VirusTotal permalink, source
file, MD5 hash, and SHA1 hash associated with the detected file.

The EICAR file is an industry-standard antivirus test file designed to
safely validate malware-detection controls without using real malware.

The VirusTotal alert confirms that the Wazuh-to-VirusTotal enrichment
workflow was functioning as intended.

## 4. Disposition

**True Positive — Authorized Security Testing**

The file was intentionally introduced as part of the laboratory
validation process and does not represent an unauthorized malware
infection.

## 5. Analyst Conclusion

The investigation demonstrates a successful endpoint threat-detection
workflow:

EICAR file creation → Wazuh File Integrity Monitoring → VirusTotal
enrichment → Wazuh security alert.

This validates the VirusTotal integration and demonstrates the use of
threat intelligence to enrich an endpoint detection.

## 6. Evidence

- `10-eicar-file-detection.png` — EICAR file creation detected by Wazuh
- `11-virustotal-alert.png` — VirusTotal alert and enrichment result in Wazuh
- `12-virustotal-enrichment.png` — VirusTotal file and hash enrichment details