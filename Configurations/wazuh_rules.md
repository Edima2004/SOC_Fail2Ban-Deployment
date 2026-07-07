# Fail2Ban Detection on Wazuh
_( On Wazuh Server )_

_path = /var/ossec/etc/rules/local_rules.xml_

```xml

<group name="fail2ban">
  <rule id="100800" level="10">
    <decoded_as>fail2ban-ban</decoded_as>
    <description>Fail2Ban blocked an IP Address</description>
  </rule>
</group>
```

<img width="1920" height="1102" alt="Screenshot_2026-06-03_22_31_49" src="https://github.com/user-attachments/assets/e72b0b86-41b6-489d-9445-5d41892563b2" />

---

_path = /var/ossec/etc/decoders/local_decoder.xml_

```xml
<decoder name="fail2ban-ban">
    <prematch>Ban</prematch>
    <regex>[(\w+)] Ban (\d+\.\d+\.\d+\.\d+) \w+</regex>
    <order>jail,srcip</order>
</decoder>
```

<img width="1920" height="1102" alt="Screenshot_2026-06-03_22_32_55" src="https://github.com/user-attachments/assets/e4a3e3ed-7ee3-40be-8713-ac66d8e967f8" />

---

_( On Wazuh Agent)_

_path = /var/ossec/etc/ossec.conf_

```xml
<localfile>
   <log_format>syslog</log_format>
   <location>/var/log/fail2ban.log</location>
</localfile>
```

<img width="1920" height="1103" alt="Screenshot from 2026-06-02 17-38-24" src="https://github.com/user-attachments/assets/0329f495-8f55-4a52-a6bc-5eb836135856" />

